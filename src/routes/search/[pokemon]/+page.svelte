
<script>
  /** @type {import('./$types').PageData} */
  export let data;
  import { onMount } from "svelte";
  import {pokemons_store} from "$lib/pokemons";

   onMount(()=>{
    let pokes = []
    if ($pokemons_store.length>2)
         pokes = JSON.parse($pokemons_store)

    
    

    if (!pokes.some(p => p.name == data.response.name))
        pokes.unshift({name:data.response.name,img:data.response.sprites['front_default']})
    console.log(pokes)
    if (pokes.length>5){
        pokes.pop()
        console.log('hej')
    }

    $pokemons_store = JSON.stringify(pokes)
    
  })

</script>

{#await data}
  <p>.. waiting</p>
{:then pokemon} 
<article class="flex-box">
  {#each Object.entries(pokemon.response.sprites) as sprites}
    {#if typeof sprites[1] == "string"}
    <img src={sprites[1]} />
    {/if}
  {/each}
</article>
<h1>{pokemon.response.name}</h1>
<section>
    Weight: {pokemon.response.weight} 
    Height: {pokemon.response.height} 
    ID: {pokemon.response.id}
</section>

{/await}  

<style>
    .flex-box{
        display:flex;
        width: 90%;
        height: 30%;
        gap: 1em;
    }
</style>


  