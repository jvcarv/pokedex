<script setup>
import 'animate.css';

function capitalizeFirstLetter(string) {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

const pokemon = defineProps(["name","xp","height","img","loading","loaded"])
</script>

<template>
    <div class="card sticky-top cardPokemonSelected" :class="loading ? '':'animate__animated animate__shakeX'">
        <div class="cardImage d-flex justify-content-center p-5">
            <img v-if="pokemon.name" :src="pokemon.img" class="card-img-top mt-5" :alt="pokemon.name">
            <img v-else src="../assets/egg_pokemon.svg" class="card-img-top mt-5" alt="Quem é esse Pokémon?!?!!">
        </div>
        <div class="card-body">
            <h3 class="card-title text-center"> {{ pokemon.name? capitalizeFirstLetter(pokemon.name) : "Quem é esse Pokémon?!?!!"}}</h3>
            <hr>
            <div class="row">
                <div class="col">
                    <strong>XP: </strong>
                    <span> {{pokemon.xp || "???"}}</span>
                </div>
                <div class="col">
                    <strong>Altura: </strong>
                    <span>{{ pokemon.height? (pokemon.height * 0.1).toFixed(2) + " m" : "???" }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .cardImage{
        background: rgb(2,0,36);
        background: radial-gradient(circle, rgba(2,0,36,0.9108018207282913) 10%, rgba(9,9,121,0.8407738095238095) 30%, rgba(0,212,255,0.6783088235294117) 40%);
    }

    .cardPokemonSelected{
        background: rgb(2,0,36);
        background: linear-gradient(180deg, rgba(2,0,36,0.9108018207282913) 2%, rgba(25, 217, 255,0.8827906162464986) 11%, rgba(0,212,255,0.6783088235294117) 60%);
    }

    img{
        max-height: 150px;
        width: auto;
    }
    
   @media(min-width: 480px){
    img{
        max-height: 300px;
        width: auto;
    }
    .cardPokemonSelected{
        height: 75vh;
    }
   } 
    
</style>