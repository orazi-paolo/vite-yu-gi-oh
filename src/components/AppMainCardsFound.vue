<script>
export default {
  data() {
    return {
      
    }
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
    <div class="bg-black pt-3 pb-3 d-flex align-items-center">
        <p class="results mb-0 ps-3">Found {{ cards.length }} cards</p>
    </div>

</template>

<style scoped>
.results{
  color: white;
}
</style>