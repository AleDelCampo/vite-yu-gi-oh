<script>

import CardFounder from './CardFounder.vue';
import { store } from '../store.js';

export default {

  name: 'AppPagination',

  components: {
    CardFounder,
  },

  data() {

    return {
      store,
    };

  },

  methods: {

    updateFilteredCards(cards) {
      this.store.cards = cards;
    },

  },
};
</script>


<template>

  <nav>  

    <div>
      <img src="https://vignette1.wikia.nocookie.net/yugiohenespanol/images/a/aa/Yugioh_anime_logo.jpg/revision/latest?cb=20130310042737&path-prefix=es" alt="">
    </div>

    <h1>Yu-Gi-Oh Api</h1>

    <CardFounder @search="updateFilteredCards"></CardFounder>

  </nav>

</template>


<style lang="scss">

nav {
  display: flex;
  align-items: center;
  justify-content: space-around;
  padding-left: 40px;
  width: 100%;
  height: 80px;
  background-color: whitesmoke;
  margin-bottom: 100px;

  img {
    width: 100px;
    transform: translateY(10%);
  }

  h1 {
    color: black;
    padding-left: 20px;
    font-size: 2em;
  }
}
</style>