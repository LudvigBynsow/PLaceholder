<script>
    let color = "black"
    let name = ''
    let epost = ""
    let lösen = ""
    function handleSubmit(){

         if (users.filter(person=>person.username == name).length==0 && users.filter(person=>person.password==lösen).length==0){
            alert("Du är nu inloggad, Välkommen "+name)}
         
         else{
            alert("Fel lösenord eller användarnamn")}
         }

         

    let colors = [{namn: "Blå", value: "blue"}, {namn: "Röd", value: "red"}, {namn: "Gul", value: "yellow"}]

    import {users_store} from "$lib/user";
    import { onMount } from "svelte";
	import { writable } from "svelte/store";
    let users = [];

    
    
    onMount(() => {
        /*Check if has more then 2 characters*/
        if($users_store.length > 2){
            users = JSON.parse($users_store);
        }
    });

</script>

<main>

    <div class="container">
        
      <h1 class="flex-container">
        Inloggning
      </h1>
      <form on:submit|preventDefault={handleSubmit} class="flex-form">
        
        <label for="name">Namn:
            <input type="text" id="name" bind:value={name}>

        </label>

        <label for="e-post">E-post:
            <input type="text" id="e-post" bind:value={epost}>
        </label>
        

        <label for="password">Lösenord:
            <input type="text" id="password" bind:value={lösen}>
        </label >
        

        <input type="submit" value="Logga in">

       <a href="/register">Register</a>


      </form>

    </div>


</main>

<style>
      .container{
            border: solid 5px rosybrown;
            border-radius: 10px;
            width: 35%;
            height: 80%;
            background-color: #3a2e3b;
            margin: auto;
            min-width: 300px;
            min-height: 500px;
        }
        h1{
            color: rgb(95, 95, 95);
        }
        .flex-container{
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-evenly;
        }
    main{
        background-image: url("https://t4.ftcdn.net/jpg/05/21/65/59/360_F_521655929_N80d5GaCQJ2VP073PfTXJTe9mkvsNtHE.jpg");
        background-size: cover;
        width: 100vw;
        height: 100vh;
        padding: 5%;
        margin: 0px;
        min-height: 500px;
        min-width: 500px;
    }
    .flex-form{
        display: flex;
        flex-direction: column;
        max-width: 200px;
        height: 300px;
        justify-content: space-between;
    }
</style>

