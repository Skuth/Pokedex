<template>
  <div class="pokemon-type">
    <p>{{ formatText(type) }}</p>
  </div>
</template>

<script>
  export default {
    props: {
      type: {
        type: String,
        required: true
      }
    },
    methods: {
      formatText(text) {
        text = String(text).toLowerCase()
        text = `${text.charAt(0).toUpperCase()}${text.slice(1)}`

        return text
      }
    }
  }
</script>

<style lang="scss" scoped>
  .pokemon-type {
    background: rgba(255, 255, 255, 0.4);
    padding: 10px 20px;
    border-radius: 100px;
    display: inline-block;
    p {
      text-align: center;
      color: #fff;
      font-size: 0.75rem;
    }
  }
</style>
