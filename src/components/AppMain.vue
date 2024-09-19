<script>
import AppMainSelect from './AppMainSelect.vue';
import AppMainCardsFound from './AppMainCardsFound.vue';
import AppMainCardsList from './AppMainCardsList.vue';
import BaseLoader from './BaseLoader.vue';
import axios from 'axios';

export default {
  data() {
    return {
      hasLoaded: false,
      selectedArchetype: '',
      apiUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php',
      cardsList: [],
    }
  },
  components: {
    AppMainSelect,
    AppMainCardsList,
    BaseLoader,
    AppMainCardsFound
  },
  methods: {
    setHasLoaded() {
      this.hasLoaded = true;
    },
    handleArchetypeChange(selectedValue) {
      this.selectedArchetype = selectedValue;
      this.hasLoaded = false;
      this.fetchCardsList(selectedValue);
    },
    fetchCardsList(archetype) {
      if (!archetype) {
        return;
      }
      axios.get(this.apiUrl, {
          params: {
            archetype: archetype,
            num: 20,
            offset: 0
          }
        })
        .then((response) => {
          console.log(response.data.data);
          this.cardsList = response.data.data;
        })
        .catch(function (error) {
          console.log(error);
        })
        .finally(() => {
          this.hasLoaded = true;
          console.log('chiamata api terminata');
        });
      }
    }
}
</script>

<template>
  <div class="container">
    <AppMainSelect @archetype-selected="handleArchetypeChange" />
    <div class="container bg-light p-5">
      <AppMainCardsFound v-if="selectedArchetype && hasLoaded"
       :cards="cardsList" />
      <AppMainCardsList v-if="selectedArchetype && hasLoaded"
       :cards="cardsList" />
    </div>
    <BaseLoader v-if="!selectedArchetype || !hasLoaded" />
  </div>
</template>

<style lang="scss" scoped>
</style>