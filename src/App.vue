<script>

import axios from 'axios';
import {store} from './store.js';
import CardList from './components/CardList.vue';

export default {
  
  data() {
    return {
      store,
    }
  },

  /*NON CREO ANCORA IL BUTTON DELLE SPECIE PER CONSIGLIO DEL PROF., SARA' LEZIONE DI DOMANI QUINDI 
  ANDREI AVANTI.*/

  created() {
    axios
      .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=48&offset=40')
      .then(res => {
        console.log(res.data.data)
        this.store.cards = res.data.data
    })
  },

  components: {
    CardList,
  },

}

</script>

<template>

  <CardList></CardList>

</template>

<style lang="scss">
</style>