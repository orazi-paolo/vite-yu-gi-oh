<script>
import AppMainCardsListItem from './AppMainCardsListItem.vue';
export default {
  data() {
    return {
      
    }
  },
  components: {
    AppMainCardsListItem
  }
}
</script>

<template>
  <div class="container bg-light p-5">
    <div class="bg-black pt-3 pb-3 d-flex align-items-center">
      <p class="results mb-0 ps-3">Found x cards</p>
    </div>
    <div class="row row-cols-5">
      <AppMainCardsListItem />
    </div>
  </div>

</template>

<style lang="scss" scoped>
.results{
  color: white;
}
</style>