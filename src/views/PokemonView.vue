<template>
  <div class="list">
    <template v-for="p in (pokemon as any)" :key="p.id">
      <div class="pokemon-card">
        <img v-on:error="handleImageError" :src="getPokemonImage(p.url)" loading="lazy">
        <strong>{{ p.name }}</strong>
    </div>
    </template>
  </div>
</template>

<script lang="ts">
  const API = 'https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0'
  export default {
    data: () => ({
      pokemon: []
    }),
    async created() {
      this.pokemon = (await this.fetchData())?.results ?? []
    },
    methods: {
      handleImageError(event: any) {
        event.target.src = 'https://placehold.co/200x200?text=404'
      },
      getPokemonImage(index: string) {
        const [, id = 1] = index.match(/pokemon\/(\d*)/) ?? []
        return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${id}.png`
      },
      async fetchData() {
        return fetch(API).then(r => r.json())
      }
    }
  }
</script>

<style>
  .list {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
  }
  .pokemon-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #eee;
    width: 200px;
    transition: all 0.1s;
  }
  .pokemon-card:hover {
    cursor: pointer;
    transform: scale(1.1);
  }
  .pokemon-card:hover img {
    filter: brightness(1.2);
  }
  .pokemon-card img {
    width: 100%;
  }
</style>