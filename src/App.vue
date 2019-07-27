<template>
    <v-app>
        <!--    <v-app-bar app>-->
        <!--      <v-toolbar-title class="headline text-uppercase">-->
        <!--        <span>Vuetify</span>-->
        <!--        <span class="font-weight-light">MATERIAL DESIGN</span>-->
        <!--      </v-toolbar-title>-->
        <!--      <v-spacer></v-spacer>-->
        <!--      <v-btn-->
        <!--        text-->
        <!--        href="https://github.com/vuetifyjs/vuetify/releases/latest"-->
        <!--        target="_blank"-->
        <!--      >-->
        <!--        <span class="mr-2">Latest Release</span>-->
        <!--      </v-btn>-->
        <!--    </v-app-bar>-->

        <v-content>
            <v-container grid-list-md>
                <v-layout>
                    <v-flex v-for="i in 2" :key="`${i}`" xs6>
                        <v-img :src="getImgUrl(image_names[i-1])" class="elevation-10" v-on:click="expandImage(i)"/>
                    </v-flex>
                    <!--                <v-flex xs6>-->
                    <!--                    <v-img src="./assets/artwork2.jpg" class="elevation-10" @click="expandImage"/>-->
                    <!--                </v-flex>-->
                    <v-flex xs3>
                        <span class="display-3">Sqoo Site</span>
                        <p class="display-1">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
                    </v-flex>
                </v-layout>
            </v-container>
            <v-overlay :value="overlay">
                <v-container grid-list-sm>
                    <v-layout>
                        <v-flex xs12>
                            <v-img v-if="current" :src="getImgUrl(image_names[current-1])" @click="overlay = false" class="elevation-10" />
                        </v-flex>
                    </v-layout>
                </v-container>
            </v-overlay>

        </v-content>
    </v-app>
</template>

<script>

    // const images = require.context('@/assets/img/covers', false, /\.png$|\.jpg$/)

    export default {
        name: 'App',
        components: {
        },
        data: () => ({
            overlay: false,
            current: null,
            image_names: ['artwork.jpg', 'artwork2.jpg']
        }),
        methods: {
            expandImage: function (num) {
                this.overlay = true
                this.current = num;
            },
            getImgUrl(pic) {
                return require('./assets/'+pic)
            }
        }
    };
</script>