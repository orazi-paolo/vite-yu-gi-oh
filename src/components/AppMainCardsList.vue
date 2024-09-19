<script>
import AppMainCardsListItem from './AppMainCardsListItem.vue';

export default {
  data() {
    return {
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
}
</script>

<template>
    <div class="row row-cols-5 gy-3" v-if="cards.length > 0">
      <!-- faccio un v-fot per mostrare le carte dell archetipo selezionato e passo gli elementi che servono alle card tramite props -->
      <AppMainCardsListItem v-for="(card) in cards" :key="card.id"
        :title = "card.name"
        :archetype = "card.archetype"
        :image = "card.card_images[0].image_url"
      />
    </div>

</template>

<style lang="scss" scoped>
</style>