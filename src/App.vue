<script>

import axios from 'axios';
import {store} from './store.js';
import CardList from './components/CardList.vue';
import CardFounder from './components/CardFounder.vue';

export default {
  
  data() {
    return {
      store,
      selectedArchetype: '',
      archetypes: [],
    }
  },

  created() {

    this.findArchetypes();

    axios.get
    ('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=48&offset=40')
      .then(res => {
      this.store.cards = res.data.data
    })
  },

  components: {
    CardList,
    CardFounder,
  },

  methods: {

    findArchetypes() {
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then(res => {
          this.archetypes = res.data;
        })
    },
  }
};
</script>


<template>

  <CardList></CardList>

</template>


<style lang="scss">

.select {
  padding: 12px;
}
</style>

