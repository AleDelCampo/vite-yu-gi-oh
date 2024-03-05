<script>

import axios from 'axios';

export default {

  data() {

    return {
      selectedArchetype: '',
      archetypes: [],
    };
  },

  created() {

    this.findArchetypes();
  },

  methods: {

    findArchetypes() {
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then(res => {
          this.archetypes = res.data;
        })
    },

    searchCards() {

      const apiIndex = this.selectedArchetype ?
        `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=48&offset=40&archetype=${this.selectedArchetype}` :
        `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=48&offset=40`;
      
      axios.get(apiIndex)
        .then(res => {
          this.$emit('search', res.data.data);
        })
    }
  }
};

</script>
    
<template>

    <div>

    <select v-model="selectedArchetype" @change="searchCards()" class="select">
      <option value="">Seleziona Archetipo</option>
      <option v-for="archetype in archetypes" :key="archetype.archetype_name" :value="archetype.archetype_name">{{ archetype.archetype_name }}</option>
    </select>

    </div>

</template>
  
  
  
<style lang="scss">
</style>