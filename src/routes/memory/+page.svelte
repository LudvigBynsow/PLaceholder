<h1 class="Rubrik">Memory</h1>

<script>
    let cards = $state([])
    let back_img ="https://image.similarpng.com/file/similarpng/very-thumbnail/2020/09/Fluffy-white-cartoon-cloud-on-blue-sky-on-transparent-PNG.png"
    let bluePoints = $state(0)
    let redPoints = $state(0)
    let flipCount = 0
    let fruit_imgs=["https://png.pngtree.com/png-vector/20240129/ourmid/pngtree-pineapple-png-with-ai-generated-png-image_11568478.png","https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/25d45014-8cc3-4c98-b02c-5a0cf3a55ddd/ddfrpyt-7b2f2fe3-9f1c-4048-98a2-f26a877dd5de.png/v1/fill/w_900,h_667/white_grapes_on_a_transparent_background__by_prussiaart_ddfrpyt-fullview.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9NjY3IiwicGF0aCI6Ii9mLzI1ZDQ1MDE0LThjYzMtNGM5OC1iMDJjLTVhMGNmM2E1NWRkZC9kZGZycHl0LTdiMmYyZmUzLTlmMWMtNDA0OC05OGEyLWYyNmE4NzdkZDVkZS5wbmciLCJ3aWR0aCI6Ijw9OTAwIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.hvaUERe-YN4cHc1ojEIczCU-2nSd_BL-kFvOrQTOtg4","https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSiCOUBwH83QNJxIACJszWZLP9wJ34Q38MC4A&s", "https://png.pngtree.com/png-vector/20241229/ourmid/pngtree-pear-slices-and-whole-isolated-on-transparent-background-png-image_14977840.png","https://png.pngtree.com/png-clipart/20250312/original/pngtree-green-lemon-png-image_20645236.png", "https://png.pngtree.com/png-clipart/20250122/original/pngtree-watermelon-transparent-background-png-image_19730741.png"]

    for (let i=0; i<12; i++){
        cards.push({img:fruit_imgs[i % 6],flipped:false,matched:false})
        
    }

    function updateScores(){
        document.getElementById("redScore").textContent = redpoints
        document.getElementById("blueScore").textContent = bluepoints
    }

    function flipCard(card){
    

    if (flipCount<2){
        flipCount+=1        
        card.flipped = true

    
    if (flipCount==2){

            let flippedcards = cards.filter(card=>(card.flipped && !card.matched))

            if (flippedcards[0].img == flippedcards[1].img){
                flippedcards[0].matched = true
                flippedcards[1].matched = true
                if (blueTurn){
                    bluePoints+=1
                }
                else{
                    redPoints+=1
                }
            }

            blueTurn=!blueTurn

            setTimeout(() =>{
            cards.forEach((card)=>{
                card.flipped = card.matched;
            });
            flipCount=0;
            cards=cards;
            

        }, 1000);
    }
    
    }}

    function getRandomInt(max) {
        return Math.floor(Math.random() * max);
    }
// Source - https://stackoverflow.com/a
// Posted by Laurens Holst, modified by community. See post 'Timeline' for change history
// Retrieved 2026-01-09, License - CC BY-SA 4.0

function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
}
shuffleArray(cards)

    let blueTurn = $state(true)
</script>

<main class="container">

    
        {#each cards as card,i}
         <div class="card" class:flipped={card.flipped} onclick={()=>flipCard(card)}>
            <img src={card.img} class="front">
            <img src={back_img} class="back">

         </div>
            
        {/each}
         

</main>


<input type="button" value="starta om">

<aside>
    <p id="redScore">
        {redPoints}
    </p>
</aside>

<aside class="blue">
    <p id="blueScore">
        {bluePoints}
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
        transition: transform 0.5s;
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
    .front{
        transform: rotateY(180deg);
    }
    .flipped{
        transform: rotateY(180deg);
        transform-style: preserve-3d;
    }
    

</style>