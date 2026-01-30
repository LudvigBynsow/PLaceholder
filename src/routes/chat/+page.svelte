<script>
    import Elizabott from "elizabot";
    import { enhance } from "$app/forms";
	import { form } from "$app/server";
    const eliza = new Elizabott();

    

    let chat = $state([{user: "Eliza", message: eliza.getInitial()}]);
    
   
 async function write(message) {
    //TODO: Add the new message to the chat
    chat.push({user: "me", message: message})

    var element = document.getElementById("visible");
    element.style.display = "flex";
    // random delay for Eliza's response time
    await new Promise((r) => setTimeout(r, 1000 + Math.random() * 1000));
    //TODO: Add Eliza's response to the chat
    chat.push({user: "Eliza", message: eliza.transform(message)})
    
    element.style.display = "none";

  }
                
</script>

<main class="container">

    <section>
        {#each chat as c}
           
            <article class={c.user}>

                <p  class="message">
                    {c["user"]}
                    <br>
                    {c.message}
                </p>
            </article>
        {/each}
        <article id="visible">
            <span class="circle">

            </span>
            <span class="circle">

            </span>
            <span class="circle">

            </span>
        </article>
    </section>

    
<!-- svelte-ignore element_implicitly_closed -->
    <form  method="post"
        use:enhance={({ formElement, formData, action, cancel }) => {
        cancel(); //don't post anything to server
        const text = formData.get("text"); // what does "text" refer to?
        write(text);

        // TODO: reset the form using _____.reset() - what do we want to reset? the element or the data?
        formElement.reset()
        }}>  
        <input name="text" placeholder="Write a message..." class="texting">  
    </form>
                

</main>

<style>
    .Eliza{
        display: flex;
        justify-self: end;
        justify-content: end;
        padding: 10px;
        border-radius: 10px;
        border: 2px solid black;
        background-color: rgba(0, 0, 0, 0.3);
        width: 90%;
        text-align: right;
    }
    .me{
        margin: 10px;
        padding: 10px;
        border-radius: 10px;
        border: 2px solid black;
        background-color: rgba(0, 0, 0, 0.1);
        width: 90%;
    }
    .message{
        
    }
    .container{
        display: grid;
        background-color: aqua;
        margin: auto;
        width: 60vw;
        height: 70vh;
        padding: 10px;
        grid-template-rows:  9fr 1fr;
        grid-template-columns: 1fr;
        overflow-y: scroll;
        border-radius: 10px;
    }
    .texting{
        margin: 10px;
        padding: 10px;
        border-radius: 10px;
        background-color: beige;
        width: 90%;
    }
    #visible{
        width: 100px;
        height: 60px;
        display: none;
        justify-content: center;
        align-items: center;
    }
    @keyframes chat-bubble{
        0%{transform: scale(1);}
        25%{transform: scale(1)}
        50%{transform: scale(1.4);}
        100%{transform: scale(1);}
    }
    .circle{
        width: 10px;
        height: 10px;
        border-radius: 50%;
        background-color: rgb(86, 86, 86);
        animation-name: chat-bubble;
        animation-duration: 1000ms;
        animation-timing-function: ease;
        animation-iteration-count: infinite;
    }
    .circle:nth-child(1){
        animation-delay: 0ms;
    }
    .circle:nth-child(2){
        animation-delay: 333ms;
    }
    .circle:nth-child(3){
        animation-delay: 666ms;
    }
</style>