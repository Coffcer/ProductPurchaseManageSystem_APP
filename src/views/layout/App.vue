<script>
import HeaderLayout from './Header.vue';
import Sidebar from './Sidebar.vue';
import FooterLayout from './Footer.vue';

export default {
    components: { HeaderLayout, Sidebar, FooterLayout },
    data () {
        return {
            userName: null
        };
    },
    created () {
        this.userName = window.userName;
    },
    events: {
        login (userName) {
            this.userName = window.userName = userName;
            window.sessionStorage.setItem('userName', this.userName);
            this.$router.go({ name: 'Order' });
        },
        logout () {
            this.userName = window.userName = null;
            window.sessionStorage.removeItem('userName');
            this.$router.go({ name: 'Home' });
        }
    }
}
</script>

<template>
<div>
    <!--Header-->
    <header-layout :user-name="userName"></header-layout>
    <!--Container-->
    <div class="page-container">
        <!--Sidebar-->
        <sidebar></sidebar>
        <!--Main-->
        <div class="page-content-wrapper">
            <div class="page-content">
                <router-view></router-view>
            </div>
        </div>
        <!--Footer-->
        <footer-layout></footer-layout>
    </div>
</div>
</template>

<style>
@font-face {
    font-family:"Open Sans";
    src:url("/static/open-sans/OpenSans-Regular.eot?") format("eot"),
        url("/static/open-sans/OpenSans-Regular.woff") format("woff"),
        url("/static/open-sans/OpenSans-Regular.ttf") format("truetype"),
        url("/static/open-sans/OpenSans-Regular.svg#OpenSans") format("svg");
}

body, h1, h2, h3, h4, h5, h6 {
    font-family: "Open Sans","Helvetica Neue",Helvetica,Arial,"Microsoft Yahei",sans-serif;
}

#app {
    position: relative;
    z-index: 0;
}

.page-title {
    font-family: "Open Sans","Helvetica Neue",Helvetica,Arial,sans-serif;
}
</style>
