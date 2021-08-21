<template>
  <div class="pokemon-card" :class="getCardColorClass()">
    <PokemonInfo
      :id="pokemon.id"
      :name="pokemon.name.english"
      :types="pokemon.type"
    />
    <div class="image">
      <img :src="getPokemonPicture(pokemon.id)" :alt="pokemon.name.english">
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      pokemon: {
        type: Object,
        required: true
      }
    },
    methods: {
      getPokemonPicture(id) {
        id = String(id).padStart(3, 0)

        return `https://raw.githubusercontent.com/fanzeyi/pokemon.json/master/images/${id}.png`
      },
      getCardColorClass() {
        if (this.pokemon && this.pokemon.type) {
          return String(this.pokemon.type[0]).toLowerCase() || ''
        }

        return '';
      }
    }
  }
</script>

<style lang="scss" scoped>
  @keyframes fadeIn {
    from {
      opacity: 0;
      margin-top: -10px;
    }
    to {
      opacity: 1;
      margin-top: 0;
    }
  }

  .pokemon-card {
    animation: fadeIn 0.5s;
    border-radius: 20px;
    display: flex;
    background: #2b2b2b;
    align-items: center;
    justify-content: space-between;
    padding: 30px;
    &.grass {
      $primary: #78C850;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.fire {
      $primary: #F08030;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.water {
      $primary: #6890F0;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.bug {
      $primary: #A8B820;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.normal {
      $primary: #A8A878;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.poison {
      $primary: #A040A0;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.electric {
      $primary: #F8D030;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.ground {
      $primary: #E0C068;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.fairy {
      $primary: #EE99AC;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.fighting {
      $primary: #C03028;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.psychic {
      $primary: #F85888;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.rock {
      $primary: #B8A038;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.ghost {
      $primary: #705898;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.ice {
      $primary: #98D8D8;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.dragon {
      $primary: #7038F8;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.dark {
      $primary: #725A4A;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.steel {
      $primary: #B8B8D2;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    &.flying {
      $primary: #9E8FC5;
      $secundary: darken($primary, 20);
      background: linear-gradient(45deg, $primary, $secundary);
    }
    .image {
      img {
        width: 120px;
      }
    }
  }
</style>
