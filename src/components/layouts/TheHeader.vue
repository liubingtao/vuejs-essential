<template>
    <div class="navbar navbar-default topnav">
        <div class="container">
            <div class="navbar-header">



                <router-link to="/" class="navbar-brand">
                    <span class="title">{{ logo.title }}</span>
                    <img :src="logo.src" :alt="logo.title">
                </router-link>
            </div>

            <div id="top-navbar-collapse" class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <li v-for="(item, index) in navList" :key="index" :class="{active: index === activeNavIndex}">
                        <a href="#" @click="changeNavIndex(index)"> {{ item }}</a>
                    </li>
                </ul>

                <div class="navbar-right">
                    <TheEntry/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    import TheEntry from "./TheEntry";

    export default {
        name: "TheHeader",
        components: {
            TheEntry
        },
        data() {
            return {
                logo: {
                    src: `${this.uploadsUrl}sites/ByvFbNlQYVwhvTyBgLdqitchoacDNznN.jpg`,
                    title: 'VueJsCaff'
                },
                navList: ['社区', '头条', '问答', '教程'],
                activeNavIndex: 0
            }
        },
        beforeCreate() {
            this.uploadsUrl = 'https://vuejscaff.com/uploads/'
        },
        methods: {
            changeNavIndex(index) {
                this.activeNavIndex = index
            }
        }
    }
</script>

<style scoped>
    .title {
        display: none;
    }

    /*.navbar-default .navbar-nav > .active > a {*/
    /*    background: rgba(0, 0, 0, .03);*/
    /*}*/
    .navbar-default .navbar-nav a:hover {
        background: rgba(0, 0, 0, .03);
    }
</style>