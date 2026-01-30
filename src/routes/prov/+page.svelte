<script>
let colors = $state(["red","blue","purple","yellow","green","orange"])
</script>

<main class="main">
    {#each colors as color,i}
    <div class="flex_box"style="background-color:{color};">
       
        <div class="box"> 
            <p class="numbers">{i+1}</p>
        </div>
        
    </div>
    {/each} 
</main>

<style>

 .main{
    justify-content: center;
    display: grid;
    margin: auto;
    row-gap: 20px;
    column-gap: 20px;
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(2,1fr);
    background-color: aliceblue;
    width: fit-content;
 }

 .flex_box{
    background-color: aqua;
    display: grid;
    flex-direction:row;
    justify-items: center;
    align-items: center;
    padding: 20px;
    gap: 50px;
    flex-wrap: wrap;
    
    height: 100px;
    width: 100px;
 }
 .box{

 }
 .numbers{
    color: black;
    display: flex;
    align-self: center;
 }
</style>