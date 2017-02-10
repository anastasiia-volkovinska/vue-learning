<template>
<div class="container">
    <h1 :class="{ red: isDesktop, blue: isMobile }">{{ name }}</h1>
    <div :class="{ desktopHeader: isDesktop, mobileHeader: isMobile }">
        <i @click="handleClick" class="fa fa-bars fa-large" aria-hidden="true"></i>
    </div>
    <ul :class="{ mobMenuList: isMobile, open: isMobileMenuOpened, closed: !isMobileMenuOpened }">
        <li v-for="item in items" ><a :href="item.link" target="_blank" :class="{ deskMenuLink: isDesktop, mobMenuLink: isMobile }">{{ item.text }}</a></li>
    </ul>
</div>
</template>

<script>
export default {
    data() {
        return {
            name: 'Header Menu',
            clicked: false,
            menuOpen: false,
        };
    },
    props: {
        items: {
            type: Array,
            required: true
        },
        type: {
            type: String,
            required: false,
            default: function() {
                return 'desktop';
            }
        }
    },
    computed: {
        isDesktop: function() {
            return (this.type == 'desktop') ? true : false;
        },
        isMobile: function() {
            return (this.type == 'mobile') ? true : false;
        },
        isMobileMenuOpened:function () {
            if (this.isDesktop) {
                return true;
            }
            if (this.isMobile) {
                return this.menuOpen;
            }
        }
    },
    methods: {
        handleClick: function() {
            this.menuOpen = !this.menuOpen;
        }
    }
}
</script>

<style>

h1 {
    color: black;
}
a {
    text-decoration: none;
}
.container {
    position: relative;
    text-align: center;
}
.red{
    color: #42b983;
}
.blue{
    color: blue;
}

.desktopHeader {
    display: none;
}

.mobileHeader {
    background-color: rgba(0, 0, 0, 0.9);
    text-align: left;
    padding: 10px;
}

.deskMenuLink {
    background-color: black;
    border-radius: 10px;
    color: white;
    padding: 15px;
    margin: 10px;
    color: #42b983;
    transition: background 0.3s;
}

.deskMenuLink:hover{
    background-color: rgba(0, 0, 0, 0.6);
}

.mobMenuList {
    flex-direction: column;
    position: absolute;
    width: 100%;
    margin: 0;
    z-index: 2;
}

.closed {
    display: none;
}

.open {
    display: flex;
    justify-content: center;
}

.mobMenuList li {
    background: #666666;
    border-bottom: solid 1px;
    padding: 5px 0;
    margin: 0;
    transition: background 0.3s;
}

.mobMenuList li:hover {
    background: #dddddd;
}

.mobMenuLink {
    position: relative;
}

.mobMenuLink::after {
    content: '';
    display: block;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 0px;
    height: 1px;
    background: green;
    transition: width .3s;
}

.mobMenuList li:hover .mobMenuLink::after {
    width: 100%;
}

.fa{
    color: white;
    cursor: pointer;
}
</style>
