<script>
import AppMainSelect from './AppMainSelect.vue';
import AppMainCardsFound from './AppMainCardsFound.vue';
import AppMainCardsList from './AppMainCardsList.vue';
import BaseLoader from './BaseLoader.vue';
import axios from 'axios';

export default {
  data() {
    return {
      // creo un flag per sapere se i dati sono stati caricati
      hasLoaded: false,
      // creo una variabile per salvare l'archetipo selezionato
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
    // creo un metodo per settare il flag hasLoaded a true
    setHasLoaded() {
      this.hasLoaded = true;
    },
    // creo un metodo per gestire il cambio di archetipo
    handleArchetypeChange(selectedValue) {
      this.selectedArchetype = selectedValue;
      this.hasLoaded = false;
      this.fetchCardsList(selectedValue);
    },
    // creo un metodo per fare la chiamata all'api
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
          // imposto la variabile cardsList con i dati ricevuti
          this.cardsList = response.data.data;
        })
        .catch(function (error) {
          console.log(error);
        })
        .finally(() => {
          // imposto il flag hasLoaded a true
          this.hasLoaded = true;
          console.log('chiamata api terminata');
        });
      }
    }
}
</script>

<template>
  <div class="container">
    <!-- creo un custom event per collegarmi con la select -->
    <AppMainSelect @archetype-selected="handleArchetypeChange" />
    <div class="container bg-light p-5">
      <!-- creo una prop per portare l'array di card nel componente di seguito -->
      <AppMainCardsFound v-if="selectedArchetype && hasLoaded"
       :cards="cardsList" />
      <!-- creo una prop per portare l'array di card nel componente di seguito -->
      <AppMainCardsList v-if="selectedArchetype && hasLoaded"
       :cards="cardsList" />
    </div>
    <BaseLoader v-if="!selectedArchetype || !hasLoaded" />
  </div>
</template>

<style lang="scss" scoped>
</style>