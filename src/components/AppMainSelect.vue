<script>
export default {
  data() {
    return {
      
    }
  },
  methods: {
    onSelectChange(event){
      this.$emit('archetypeSelected', event.target.value);
    }
  }
}
</script>

<template>
  <select class="form-select mt-3 mb-3 ms-3" @change="onSelectChange($event)">
  <option selected>Select an archetype</option>
  <option value="Dark Magician">Dark Magician</option>
  <option value="Prank-Kids">Prank-Kids</option>
  <option value="Blue-Eyes">Blue-Eyes</option>
</select>
</template>

<style lang="scss" scoped>
select{
  width: auto !important;
}
</style>