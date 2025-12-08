<h1 class="Rubrik">Memory</h1>

<script>
    let cards = $state([])
    let back_img ="https://image.similarpng.com/file/similarpng/very-thumbnail/2020/09/Fluffy-white-cartoon-cloud-on-blue-sky-on-transparent-PNG.png"
    let bluePoints = 0
    let redPoints = 0
    for (let i=0; i<12; i++){
        cards.push({img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSiCOUBwH83QNJxIACJszWZLP9wJ34Q38MC4A&s",flipped:false,matched:false})
        
    }

    function updateScores(){
        document.getElementById("redScore").textContent = redpoints
        document.getElementById("blueScore").textContent = bluepoints
    }

    let blueTurn = true
</script>

<main class="container">

    
        {#each cards as card,i}
         <div class="card" class:flipped={card.flipped}>
            <img src={card.img} class="front">
            <img src={back_img} class="back">

         </div>
            
        {/each}


</main>

<aside>
    <p id="redScore">
        0
    </p>
</aside>

<aside class="blue">
    <p id="blueScore">
        0
    </p>
</aside>

<aside class="turn" class:blue = {blueTurn}>

</aside>

<style>
    .Rubrik{
        justify-content: center;
        display: flex;
    }
    .container{
        display:grid;
    
        grid-template-columns:repeat(3,100px);
        grid-template-rows:repeat(4,100px);
        margin: auto;
        width: fit-content;
        row-gap: 20px;
        column-gap: 40px;
    }
    .card{
        border: 1px solid rgb(0, 0, 0);
        height: 100%;
        width: 100%;
        position: relative;
        backface-visibility: hidden;
    }
    .card img {
        width: 100%;
        height: 100%;
        position: absolute;
    }
    
    aside{
        width: 100px;
        height: 100px;
        position: fixed;
        bottom: 10px;
        right: 10px;
        background-color: red;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    p{
        font-size: 30px;
    }
    .blue{
        left: 10px;
        background-color: blue;
    }
    .turn{
        box-shadow: 0 0 10px 10px yellowgreen;
        z-index: -1;
    }
    .back{
        transform: rotatey(180deg);
    }
    .front{
        transform: rotatey(180deg);
    }
</style>