<template>
  <h1 class="pokemon-name">{{ name }}</h1>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  .pokemon-name {
    color: #fff;
    font-size: 1.5rem;
  }
</style>
