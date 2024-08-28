<script setup>
function capitalizeFirstLetter(string) {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

const pokemon = defineProps(["name", "urlBaseSvg"])

</script>

<template>
  <div class="col-4">
    <div class="card p-2 mb-3" id="cardListPokemon">
        <p class="text-center"><b>{{capitalizeFirstLetter(pokemon.name)}}</b></p>
        <img :src="urlBaseSvg" alt="Imagem do pokémon" class="card-top-image mt-0" height="80">
    </div>
  </div>
</template>

<style scoped>
  #cardListPokemon{
    background: rgb(2,0,36);
    background: radial-gradient(circle, rgba(2,0,36,1) 6%, rgba(9,9,121,0.8407738095238095) 20%, rgba(115, 187, 238, 0.693) 50%);
    cursor: pointer;
    transition: 1s;
  }

  #cardListPokemon:hover{
    background: rgb(2,0,36);
    background: radial-gradient(circle, rgba(2,0,36,0.9108018207282913) 10%, rgba(9,9,121,0.8407738095238095) 30%, rgba(0,212,255,0.6783088235294117) 65%);
    transition: 1s;
  }

  #cardListPokemon img:hover{
    padding: .3rem;
  }

</style>