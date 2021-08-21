<template>
  <div class="pokemon-info">
    <PokemonName :name="name" />
    <span class="id">#{{ String(id).padStart(3, 0) }}</span>
    <div class="types">
      <PokemonType
        v-for="type in types"
        :key="type"
        :type="type"
        class="type"
      />
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      name: {
        type: String,
        required: true
      },
      id: {
        type: Number,
        required: true
      },
      types: {
        type: Array,
        required: true
      }
    }
  }
</script>

<style lang="scss" scoped>
  .pokemon-info {
    position: relative;
    .id {
      position: absolute;
      font-size: 4.5rem;
      top: 50%;
      color: rgba(255, 255, 255, 0.2);
      font-weight: 600;
      transform: translateY(-50%);
      z-index: 1;
    }
    .types {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      margin-top: 10px;
      .type {
        margin-top: 10px;
      }
    }
  }
</style>
