 
 <script>
import { goto } from '$app/navigation';
import { onMount } from 'svelte';
   import {pokemons_store} from "$lib/pokemons";
   let pokemons = $state([])
  // Funktion som hanterar formulärets submit-händelse
  function handleSubmit(e) {
    // Förhindra att sidan laddas om (standardbeteende för formulär)
    e.preventDefault();


    
    // Skapa ett FormData-objekt från formuläret
    const formData = new FormData(e.target);
    
    // Hämta värdet från input-fältet med name="search"
    const search = formData.get('search');

    
    // Navigera till den dynamiska routen /search/[pokemon]
    goto('/search/' + search);
  }


   onMount(()=>{
    //if ($pokemons_store.length>2)
        
    
       


     pokemons_store.subscribe(()=>{        
        pokemons = JSON.parse($pokemons_store)


  })
    console.log('p:',pokemons)

})

 </script>
 
 <form onsubmit={handleSubmit}>
        <input type="text" name="search" placeholder="Sök upp en pokemon" class="write" />
    </form>

 <footer>
        {#each pokemons as pokemon}
        
        
        <img src={pokemon.img} alt={pokemon.name} onclick={goto('/search/' + pokemon.name)}>
            
        {/each}
 </footer>


<style>
    .write{
    display: flex;
    background-color: rgba(255, 255, 255, 0.2);
    align-self: center;
    justify-self: center;
    margin: 10px;
    padding: 10px;
    border-radius: 10px;
    width: 50vw;
}
    footer{
        display: flex;
        width: 100%;
        justify-content: center;
        align-content: end;
        
    }

</style>