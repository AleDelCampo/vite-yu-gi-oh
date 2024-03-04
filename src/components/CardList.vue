<script>

import AppPagination from "./AppPagination.vue";
import CardItem from "./CardItem.vue";
import {store} from '../store.js';

export default {
    
    name: 'CardList',

    components:  {
        AppPagination,
        CardItem,
    },

    data() {
        return  {
            store,
        }
    }
}

</script>

<template>

    <AppPagination></AppPagination>

    <div class="container">
        <ul>
            <CardItem 
                v-for="currentCard in store.cards"
                :card="currentCard"
            ></CardItem>
           
        </ul>
    </div>

</template>

<style lang="scss">

ul {
    list-style-type: none;
    display: flex;
    flex-flow: row wrap;
    gap: 20px;
}

</style>