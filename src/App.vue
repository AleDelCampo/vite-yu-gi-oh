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

  /*Descrizione:
  Continuate a lavorare nella stessa repo di ieri e aggiungete una select per filtrare i risultati in base all’archetipo.
  Le option della select devono essere popolate dinamicamente chiamando questo endpoint dell'api:
  https://db.ygoprodeck.com/api/v7/archetypes.php
  Quando l'utente seleziona un valore dalla lista, viene effettuata una chiamata alle API con l'archetipo selezionato.
  Bonus:
  Creare un componente che mostri il numero totale di risultati ottenuti.*/

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

