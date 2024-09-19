<script>
import AppMainCardsListItem from './AppMainCardsListItem.vue';
import axios from 'axios';

export default {
  data() {
    return {
      cardsList: [],
      apiUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php',
    }
  },
  components: {
    AppMainCardsListItem
  },
  props: {
    cards: {
      type: Array,
      required: true
    }
  },
  methods: {
    fetchCardsList() {
      this.fetchCards(this.selectedArchetype); 
    }
  }
}
</script>

<template>
  <div class="container bg-light p-5">
    <div class="bg-black pt-3 pb-3 d-flex align-items-center">
      <p class="results mb-0 ps-3">Found {{ cards.length }} cards</p>
    </div>
    <div class="row row-cols-5 gy-3" v-if="cards.length > 0">
      <AppMainCardsListItem v-for="(card) in cards" :key="card.id"
        :title = "card.name"
        :archetype = "card.archetype"
        :image = "card.card_images[0].image_url"
      />
    </div>
  </div>

</template>

<style lang="scss" scoped>
.results{
  color: white;
}
</style>