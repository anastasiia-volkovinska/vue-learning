
<template>
<div id="app">
    <header-menu :items="headerItems" :type="headerType"></header-menu>
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
        <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
        <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
        <li><a href="https://gitter.im/vuejs/vue" target="_blank">Gitter Chat</a></li>
        <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
        <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
        <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
        <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
        <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
</div>
</template>

<script>
import Nastya from './Nastya.vue';

export default {
    name: 'app',
    data() {
        return {
            msg: 'I am Nastya Component!',
            childMsg: 'Hey I am here in root component!',
            headerItems: [{
                    link: '#',
                    text: 'Home'
                },
                {
                    link: '#',
                    text: 'About us'
                },
                {
                    link: '#',
                    text: 'Products'
                },
                {
                    link: '#',
                    text: 'News'
                },
                {
                    link: '#',
                    text: 'Comments'
                }
            ],
            headerType: null
        }
    },
    methods: {
        onResize: function() {
            let currentWidth = window.innerWidth;
            if (currentWidth < 600) {
                this.headerType = 'mobile';
            } else {
                this.headerType = 'desktop';
            }
        }
    },
    components: {
        headerMenu: Nastya
    },
    beforeMount: function() {
        this.onResize();
        window.addEventListener('resize', this.onResize.bind(this));
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

h1,
h2 {
    font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
