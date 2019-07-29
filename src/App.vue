<template>
    <v-app>
        <v-content>
            <v-container grid-list-md>
                <v-layout>
                    <vue-instagram v-if="access_key" :token="access_key">
                        <template slot="feeds" slot-scope="props">
                            <v-img :src="props.feed.images.low_resolution.url" alt="Image from Instagram" @click="expandImage(props.feed.images)"/>
<!--                            <span>X: {{props.feed.images}}</span>-->
                        </template>
                    </vue-instagram>
<!--                    <v-flex v-for="i in 2" :key="`${i}`" xs6>-->
<!--                        <v-img v-bind:contain="true" :src="getImgUrl(image_names[i-1])" class="elevation-10" v-on:click="expandImage(i)"/>-->
<!--                    </v-flex>-->
                    <!--                <v-flex xs6>-->
                    <!--                    <v-img src="./assets/artwork2.jpg" class="elevation-10" @click="expandImage"/>-->
                    <!--                </v-flex>-->
                    <v-flex xs3>
                        <span class="display-3">Sqoo Site</span>
                        <p class="display-1">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
                    </v-flex>
                </v-layout>
            </v-container>

        </v-content>
        <v-overlay :value="overlay">
            <v-container grid-list-sm fluid>
                <v-layout>
                    <v-flex xs12>
                        <v-img v-if="current" v-bind:contain="true" :src="current.standard_resolution.url" @click="overlay = false" class="elevation-10" />
                    </v-flex>
                </v-layout>
            </v-container>
        </v-overlay>

    </v-app>
</template>

<script>
    import VueInstagram from 'vue-instagram';

    // const images = require.context('@/assets/img/covers', false, /\.png$|\.jpg$/)

    const access_key = require('./assets/access-token').key;

    export default {
        name: 'App',
        components: {
            VueInstagram
        },
        data: () => ({
            overlay: false,
            current: null,
            image_names: ['artwork.jpg', 'artwork2.jpg'],
            access_key: access_key
        }),
        methods: {
            expandImage: function (image) {
                this.overlay = true
                this.current = image;
            },
            getImgUrl(pic) {
                return require('./assets/'+pic)
            }
        },
    };
</script>