<script setup>
import {onMounted, reactive, ref, computed} from 'vue';
import ListPokemons from '@/components/ListPokemons.vue';
import CardPokemonSelected from '@/components/CardPokemonSelected.vue';

let pokemons = reactive({list:[]});
let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeApi/sprites/master/sprites/pokemon/other/dream-world/")
let searchPokemonField = ref("");
let pokemonSelected = reactive(ref());
let loading = ref(false);
let loaded = ref(true);

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=649&offset=0")
  .then(res => res.json())
  .then(data => pokemons.list = data.results);
})

const pokemonsFiltered = computed(() => {
  if(searchPokemonField.value){
    return pokemons.list.filter(pokemon =>
      pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    )
  }
  return pokemons.list;
})

const selectPokemon = async (pokemon) => {
  loading.value = true;
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(res => pokemonSelected.value = res)
  .catch(err => alert(err))
  .finally(()=>{
    loading.value = false;
    loaded.value = false;
  });
}


</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <CardPokemonSelected
          :name="pokemonSelected?.name"
          :xp="pokemonSelected?.base_experience"
          :height="pokemonSelected?.height"
          :img="pokemonSelected?.sprites.other.dream_world.front_default"
          :loading='loading'
          :loaded="loaded"/>
        </div>
        <div class="col-sm-12 col-md-6">
          <div class="card card-list">
            <div class="card-body row">
              <div class="mb-3">
                <label hidden for="searchPokemonField" class="form-label">Pesquisar</label>
                <input v-model="searchPokemonField" type="text" class="form-control" id="searchPokemonField" placeholder="Pesquisar...">
              </div>
              <ListPokemons
              v-for="pokemon in pokemonsFiltered"
              :key="pokemon.name"
              :name="pokemon.name"
              :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
              @click="selectPokemon(pokemon)"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

  .card-list {
    max-height: 75vh;
    overflow-y: scroll;
    overflow-x: hidden;
  }
  
</style>
