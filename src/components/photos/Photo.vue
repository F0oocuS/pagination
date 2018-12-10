<template>
    <div class="photo">
        <img v-bind:src="url" alt="" class="photo__image">
    </div>
</template>

<script>
    export default {
        props: ['item'],
        data() {
            return {
                url: `https://farm${this.item.farm}.staticflickr.com/${this.item.server}/${this.item.id}_${this.item.secret}.jpg`
            }
        }
    }
</script>

<style lang="scss">
    .photo {
        padding: 15px;
        width: calc(100% / 3);
        img {
            width: 100%;
            height: 100%;
            max-height: 300px;
            object-fit: cover;
        }
        @media(max-width: 991px) {
            width: 50%;
        }
        @media(max-width: 767px) {
            width: 100%;
        }
    }
</style>