<template>
  <Container v-if="pokemons.length">
    <div class="pokemon-container" >
        <PokemonCard
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        class="pokemon-card"
        :pokemon="pokemon"
      />
    </div>

    <div class="load-container">
      <p @click="page = page + 1">Carregar mais</p>
    </div>
  </Container>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const apiUrl = 'https://raw.githubusercontent.com/fanzeyi/pokemon.json/master/pokedex.json'

      const data = await $axios.get(apiUrl)
        .then(res => res.data)
        .catch(() => {})

      if (!data) return {};

      return {
        pokemonsData: data
      }
  },
  data() {
    return {
      pokemons: [],
      page: 1
    }
  },
  watch: {
    page() {
      this.getPokemonList()
    }
  },
  mounted() {
    this.getPokemonList()
  },
  methods: {
    getPokemonList() {
      const start = 16 * (this.page - 1)
      const skip = 16 * this.page

      const pokemons = this.pokemonsData.slice(start, skip)

      this.pokemons = [
        ...this.pokemons,
        ...pokemons
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .pokemon-container {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 40px;
    @media (max-width: 1420px) {
      grid-template-columns: repeat(3, 1fr);
    }
    @media (max-width: 1060px) {
      grid-template-columns: repeat(2, 1fr);
    }
    @media (max-width: 720px) {
      grid-template-columns: 1fr;
    }
  }
  .load-container {
    display: grid;
    place-items: center;
    margin: 20px 0;
    margin-top: 40px;
    p {
      cursor: pointer;
      border: 2px solid #111;
      padding: 10px 25px;
      border-radius: 100px;
      transition: color 0.5s, background 0.5s;
      &:hover {
        color: #fff;
        background: #111;
      }
    }
  }
</style>
