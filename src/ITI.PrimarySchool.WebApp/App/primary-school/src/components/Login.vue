<template>
    <div>
        <div class="text-center">
            <div class="page-header">
                <h1>Bienvenue sur ITI.PrimarySchool</h1>
            </div>

            <button type="button" @click="login('Google')" class="btn btn-lg btn-block btn-primary"><i class="fa fa-google" aria-hidden="true"></i> Se connecter via Google</button>
            <button type="button" @click="login('GitHub')" class="btn btn-lg btn-block btn-primary"><i class="fa fa-github" aria-hidden="true"></i> Se connecter via GitHub</button>
            <button type="button" @click="login('Base')" class="btn btn-lg btn-block btn-default">Se connecter via ITI.PrimarySchool</button>
        </div>
    </div>
</template>

<script>
    import AuthService from '../services/AuthService'
    import Vue from 'vue'
    import $ from 'jquery'

    export default {
        data() {
            return {
                endpoint: null
            }
        },

        mounted() {
            AuthService.registerAuthenticatedCallback(() => this.onAuthenticated());
        },

        beforeDestroy() {
            AuthService.removeAuthenticatedCallback(() => this.onAuthenticated());
        },

        methods: {
            login(provider) {
                AuthService.login(provider);
            },

            onAuthenticated() {
                 this.$router.replace('/');
            }
        }
    }
</script>

<style lang="less">
    iframe {
        width: 100%;
        height: 600px;
    }
</style>