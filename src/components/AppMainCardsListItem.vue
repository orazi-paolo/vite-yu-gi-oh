<script>
export default {
  data() {
    return {
      
    }
  },
  props: {
    title: {
      type: String,
      required: true
    },
    archetype: {
      type: String,
      required: false
    },
    image: {
      type: String,
      required: true
    }
  }
}
</script>

<template>
    <div class="card border-0">
        <img :src="image" class="card-img-top" :alt="title">
        <div class="card-body">
          <h5 class="card-title text-center">{{ title }}</h5>
          <p class="card-text text-center">{{ archetype }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card-body{
  background-color: #d48f3c;
  .card-title{
    color: white;
  }
}
</style>