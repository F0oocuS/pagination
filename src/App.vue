<template>
    <div class="wrapper">
        <appHeader :sendGet="sendGet"></appHeader>
        <div class="container">
            <appPhotos :photos="showingPhotos" :showMorePhotos="showMorePhotos" :isShowBtn="showingPhotos.length"></appPhotos>
        </div>
        <appFooter></appFooter>
    </div>
</template>

<script>
    import Header from './components/Header.vue';
    import Photos from './components/photos/Photos.vue';
    import Footer from './components/Footer.vue';

    let key = '9ba801aac4f1de88996098d85fe3ca6b';

    export default {
        data() {
            return {
                showingPhotos: [],
                photos: []
            }
        },
        components: {
            appHeader: Header,
            appPhotos: Photos,
            appFooter: Footer
        },
        methods: {
            sendGet(params) {
                this.photos = [];
                this.showingPhotos = [];
                let url = `https://api.flickr.com/services/rest/?method=flickr.photos.search&api_key=${key}&tags=${params}&format=json&nojsoncallback=1`;

                this.$http.get(url).then(
                    response => {
                        this.photos = response.body.photos.photo;
                        this.showingPhotos = this.photos.slice(0, 10);
                    },
                    error => {
                        console.log(error);
                    });
            },
            showMorePhotos() {
                let index = this.showingPhotos.length;
                let newElement = this.photos.slice(index + 1, index + 11);

                this.showingPhotos = this.showingPhotos.concat(newElement);
            }
        }
    }
</script>

<style lang="scss">
    * {
        box-sizing: border-box;
        font-family: 'Roboto', sans-serif;
    }
    body {
        margin: 0;
    }
    .wrapper {
        display: flex;
        flex-direction: column;
        min-height: 100vh;
    }
    .container {
        width: 100%;
        max-width: 1200px;
        padding-left: 15px;
        padding-right: 15px;
        margin: 0 auto;
    }
</style>
