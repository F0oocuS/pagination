<template>
    <div class="photos">
        <h3 class="photos__title">Search result</h3>

        <div class="photos__wrapper">
            <appPhoto v-for="(photo, index) in photos" :item="photo"></appPhoto>
        </div>

        <button v-if="isShowBtn" class="photos__show-more" v-on:click="showMorePhotos()">Show more photos</button>
    </div>
</template>

<script>
    import Photo from './Photo.vue';

    export default {
        props: ['photos', 'showMorePhotos', 'isShowBtn'],
        components: {
            appPhoto: Photo
        }
    }
</script>

<style lang="scss">
    .photos {
        margin-left: -15px;
        margin-right: -15px;
        &__title {
            padding-left: 15px;
            padding-right: 15px;
            text-align: center;
            font-size: 26px;
        }
        &__wrapper {
            display: flex;
            flex-wrap: wrap;
        }
        &__show-more {
            display: block;
            margin: 0 auto 15px;
            padding: 15px;
            max-width: 280px;
            width: 100%;
            font-size: 18px;
            line-height: 1;
            color: #002752;
            background-color: #cce5ff;
            border: 2px solid #002752;
            border-radius: 10px;
            text-transform: uppercase;
            cursor: pointer;
            transition: .3s all ease;
            &:hover, &:focus, &:active {
                outline: none;
            }
            &:hover {
                background-color: #002752;
                color: #fff;
            }
        }
    }
</style>