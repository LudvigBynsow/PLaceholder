<script>
     
  // Importera goto-funktionen för att navigera mellan sidor
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



</script>


<main>

    <slot>

    </slot>

  

   
</main>

<div class="backdrop">

</div>


<style>
main{
    display: flex;

    height: 100vh;
    width: 80vw;
    background-color: rgba(255, 255, 255, 0.8);
    margin: 5vh auto;
    border-radius: 10px;
    border: 2px solid black;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
.backdrop{
    width: 100vw;
    height: 100vh;
    background-image: url("https://imageio.forbes.com/specials-images/imageserve/604202ff091b6539cb90fcbc/The-backs-of-a-number-of-Pok-mon-cards-/960x0.jpg?format=jpg&width=960");
    background-size: cover;
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
    filter: blur(5px);
}
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

</style>