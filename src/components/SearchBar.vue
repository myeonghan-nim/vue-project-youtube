<template>
  <div class="text-center">
    <input type="text" class="w-75" @input="onInput">
  </div>
</template>

<script>
export default {
  name: 'SearchBar',

  methods: {
    onInput(e) {
      // emit serve event to parent component
      this.$emit('inputChange', e.target.value)
    }
  },
}
</script>

<style>

</style>