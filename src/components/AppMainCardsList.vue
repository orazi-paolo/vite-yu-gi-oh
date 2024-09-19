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
  methods: {
    getCardsList() {
      axios.get(this.apiUrl, {
          params: {
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
          console.log('chiamata api terminata')
        });  

    }
  },
  created() {
    setTimeout(() => {
      this.getCardsList();
      this.$emit('hasLoaded');

    }, 2000);
  }
}
</script>

<template>
  <div class="container bg-light p-5">
    <div class="bg-black pt-3 pb-3 d-flex align-items-center">
      <p class="results mb-0 ps-3">Found {{ cardsList.length }} cards</p>
    </div>
    <div class="row row-cols-5 gy-3">
      <AppMainCardsListItem v-for="(card) in cardsList" :key="card.id"
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