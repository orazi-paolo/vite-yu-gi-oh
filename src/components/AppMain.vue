<script>
import AppMainSelect from './AppMainSelect.vue';
import AppMainCardsList from './AppMainCardsList.vue';
import BaseLoader from './BaseLoader.vue';

export default {
  data() {
    return {
      
    }
  },
  components: {
    AppMainSelect,
    AppMainCardsList,
    BaseLoader
  }
}
</script>

<template>
  <div class="container">
    <AppMainSelect />
    <BaseLoader />
    <AppMainCardsList />
  </div>
</template>

<style lang="scss" scoped>
</style>