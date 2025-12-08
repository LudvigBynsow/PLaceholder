
<script>
    import { fade } from 'svelte/transition'

    let varor = $state([{ name:"Äpplen",köpt:true,prio:1}])

    
    let ny_vara = ""

    let new_vara = ""
    function handleSubmit(e){
        e.preventDefault()
        if (ny_vara != ""){
                 varor.push({name: ny_vara,köpt:true,prio:1})
             }
        }

    function handleSubmitvara(e){
        e.preventDefault()
        if (new_vara != ""){
                 varor.push({name: new_vara,köpt:false})
             }
        }

    function deletevara(i){
        varor.splice(i,1)
    }

    function deletevaror(i){
        varor.splice(i,1)
    }

    function move(i){
        varor[i].köpt = !varor[i].köpt
    }
    $effect(()=> varor.sort((a,b)=> a.prio-b.prio))

</script>

<main class="container">
    <h1 class="title">
        Shoppinglist
    </h1>

    <div class="categories_container">
        <section >
            <h2 class="varor_köpa">
                Varor att köpa
            </h2>
            <ol class="organiserad_lista">

                {#each varor as vara,i}
                {#if !vara.köpt}
                   <li class="lista" transition:fade>
                    {vara.name}
                    <input type="button" value="Ta bort" onclick={()=>deletevaror(i)}>
                    <input type="button" value="Flytta över" onclick={()=>move(i)}>
                    <input type="number" bind:value={vara.prio}>
                </li> 
                {/if}
                    
                {/each}
                
            </ol>
            <form onsubmit={handleSubmitvara}>
                    <label for="New">Ny vara</label>
                    <input type="text" id="New" bind:value={new_vara}>

                    <input type="submit" value="Lägg till">
        </section>

        <section >
            <h2 class="varor_köpt">
                Köpta varor
            </h2>
            <ul class="ickeorganiserad_lista">
                {#each varor as vara,i}
                {#if vara.köpt}
                    <li class="list" transition:fade>
                        {vara.name} 
                        <input type="button" value="Ta bort" onclick={()=>deletevara(i)}>
                        <input type="button" value="Flytta över" onclick={()=>move(i)}>
                    </li>
                    {/if}
                {/each}
            </ul>
                <form onsubmit={handleSubmit} >
                    <label for="New">Ny vara</label>
                    <input type="text" id="New" bind:value={ny_vara}>
                    <input type="submit" value="Lägg till">
                </form>
            
        </section>
    </div>



</main>

<style>

.container{
    background-color: aqua;
    width: 60vw;
    height: 70vh;
    border-radius: 20px;        
    display: grid;
    grid-template-rows: 1fr 9fr 1fr;
    justify-items: center;
    align-items: start;
}

.varor_köpa{
    text-align: center;
    background-color: rgba(0,0,0,0.1);
    font-size: 22px;
    padding: 10px;
    margin: 0.1px;
}
.varor_köpt{
    text-align: center;
    background-color: rgba(0,0,0,0.3);
    font-size: 22px;
    padding: 10px;
    margin: 0.1px;
}

.organiserad_lista{
    list-style-type: upper-alpha;
}
.ickeorganiserad_lista{
    list-style-type: square;
}
.title{
    background-color: #00c8c8;
    border-radius: 20px;
}

.categories_container{
    height: 100%;
    background-color: rgba(0,0,0,0.2);
    width: 100%;
    display: grid;
    grid-template-columns: repeat(2,1fr);
    gap: 10px;
}

.categories_container section:nth-child(1){
    background-color: rgba(0,0,0,0.1);

}
.categories_container section:nth-child(2){
    background-color: rgba(0,0,0,0.3);
    
}

.list{
    border: 1px solid white;
}
.lista{
    border: 1px solid white;
}
</style>

