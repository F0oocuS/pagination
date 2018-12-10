<template>
    <header class="header">
        <div class="header__logo">
            LOGO
        </div>

        <div class="header__search search">
            <input type="text" class="search__input" v-model="inputValue">

            <button class="search__button" type="button" v-on:click="sendGet(inputValue)">Search</button>
        </div>
    </header>
</template>

<script>
    export default {
        props: ['sendGet'],
        data() {
            return {
                inputValue: ''
            }
        }
    }
</script>

<style lang="scss">
    .header {
        padding: 15px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        background-color: #cce5ff;
        &__logo {
            font-family: 'Black And White Picture', sans-serif;
            font-size: 42px;
            line-height: 1;
            color: #002752;
        }
        .search {
            display: flex;
            border-radius: 10px;
            overflow: hidden;
            border: 2px solid #002752;
            &__input {
                padding: 10px;
                font-size: 16px;
                color: #5d5d5d;
                border: none;
                &:hover, &:focus, &:active {
                    outline: none;
                }
            }
            &__button {
                padding: 10px;
                font-size: 18px;
                color: #002752;
                text-transform: uppercase;
                border: none;
                background-color: #cce5ff;
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
    }
    @media(max-width: 540px) {
        .header {
            flex-direction: column;
        }
    }
</style>