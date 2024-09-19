<script>
import AppMainSelect from './AppMainSelect.vue';
import AppMainCardsList from './AppMainCardsList.vue';
import BaseLoader from './BaseLoader.vue';

export default {
  data() {
    return {
      hasLoaded: false,
    }
  },
  components: {
    AppMainSelect,
    AppMainCardsList,
    BaseLoader
  },
  methods: {
    setHasLoaded() {
      this.hasLoaded = true;
    }
  },
}
</script>

<template>
  <div class="container">
    <AppMainSelect />
    <AppMainCardsList @hasLoaded="setHasLoaded" />
    <BaseLoader v-if="!hasLoaded"/>
  </div>
</template>

<style lang="scss" scoped>
</style>