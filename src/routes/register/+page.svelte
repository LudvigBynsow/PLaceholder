<script>
	import { browser } from "$app/environment";

    let color = "black"
    let name = ''
    let epost = ""
    let lösen = ""
    function handleSubmit(){
         /*alert("Välkommen "+name+", "+epost+", "+lösen+".")*/
         if (users.filter(person=>person.username == name).length==0){
            let new_user = {username: name, password: lösen, email: epost, color: color};
            users = [...users, new_user];
            $users_store = JSON.stringify(users);
         }
         else{
            alert("Name is taken.")
         }
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
        <div style="width: 100px; height: 100px; border-radius: 50%; overflow:hidden; background-color:{color};"></div>
      <h1 class="flex-container">
        registrering
      </h1>
      <form on:submit|preventDefault={handleSubmit} >
        
        <label for="name">Namn:</label>
        <input type="text" id="name" bind:value={name}>

        <label for="e-post">E-post:</label>
        <input type="text" id="e-post" bind:value={epost}>

        <label for="password">Lösenord</label >
        <input type="text" id="password" bind:value={lösen}>

        <label for="color">Favoritfärg</label>
        <select id="color" bind:value={color}>
            <option value="blue">Blå</option>
            <option value="yellow">Gul</option>
            <option value="red">Röd</option>
            
        </select>

        <input type="submit" value="Registrera">

        Har du redan ett konto?
        <a href="/login">Logga in</a>

       


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
</style>

