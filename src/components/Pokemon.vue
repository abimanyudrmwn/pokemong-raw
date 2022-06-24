<template>
  <div class="container">
    <h1>Info Pokemon Maseh</h1>
    <p>Created by <a href="https://instagram.com/abimanyudrmwn">@abimanyudrmwn</a> | Api References: <a href="https://pokeapi.co/">PokeAPI</a></p>
    <PokemonSearch 
      :apiUrl="apiUrl" 
      @setPokemonUrl="setPokemonUrl" />
    <PokemonList 
      :imageUrl="imageUrl" 
      :apiUrl="apiUrl"
      @setPokemonUrl="setPokemonUrl" />
    <PokemonDetail 
      v-if="showDetail"
      :pokemonUrl="pokemonUrl"
      :imageUrl="imageUrl"
      @closeDetail="closeDetail" />
  </div>
</template>

<script>
  import PokemonSearch from './PokemonSearch.vue';
  import PokemonList from './PokemonList.vue';
  import PokemonDetail from './PokemonDetail.vue';

  export default {
    data: () => {
      return {
        imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
        apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
        pokemonUrl: '',
        showDetail: false
      }
    },
    components: {
      PokemonSearch,
      PokemonList,
      PokemonDetail
    },
    methods: {
      setPokemonUrl(url) {
        this.pokemonUrl = url;
        this.showDetail = true;
      },
      closeDetail() {
        this.pokemonUrl = '';
        this.showDetail = false;
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 10px;
    width: calc(100% - 20px);
    min-height: calc(100vh - 20px);
    background: radial-gradient(#156F99, #0A2E50);

    font-family: 'Roboto', arial;
    font-size: 1rem;
    font-weight: normal;
  }

  h1 { color: #efefef; }
  p {
    color: #efefef;
    margin-top: -10px;
  }
  a {
    color:#efefef;
    background-color:#156F99; 
    border-radius: 2px;
    padding: 1px;
    font-size: 15px;
  }
</style>
