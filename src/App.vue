<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
  data() {
    return {
    }
  },
  components: {
    AppHeader,
    AppMain
  }
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss">
@use "bootstrap/scss/bootstrap";
body{
  background-color: #d48f3c;
}

</style>
