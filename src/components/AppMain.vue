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
    <h1>
        sono il main
    </h1>
    <BaseLoader />
    <AppMainSelect />
    <AppMainCardsList />
</template>

<style lang="scss" scoped>
</style>