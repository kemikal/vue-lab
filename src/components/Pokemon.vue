<template>
  <div>
    <h1>Pokemon</h1>

        <div v-if="pokemon.name != null" style="margin-bottom: 20px; border: 1px solid black">
            Name: {{ pokemon.name }}<br />
            Weight: {{ pokemon.weight }}<br />
            Height: {{ pokemon.height }}<br />
        </div>

        <div>
            <a v-for="pokemon in pokemons" :key="pokemon.name" @click="getPokemon(pokemon.url)">{{ pokemon.name }}<br /></a>
        </div>

      

    </div>
</template>

<script>
export default {
    name: "Pokemon",
    data() {
        return {
            pokemons: [],
            pokemon: {},
        }
    },
    created() {
        console.log("Created!");

        fetch("https://pokeapi.co/api/v2/pokemon")
        .then(res => res.json())
        .then(data => {
            console.log("pokemons", data.results);
            this.pokemons = data.results;
        })
    },
    mounted() {
        console.log("Mounted!");
    }, 
    updated() {
        console.log("Updated!");
    },
    methods: {
        getPokemon(url) {
            console.log("getPokemon", url);
            fetch(url)
            .then(res => res.json())
            .then(data => {
                console.log("Pokemon data", data);
                this.pokemon = data;
            })
        }
    }
}
</script>

<style>

</style>