<header>
    <h1>Photoapp</h1>
    <h2>Denna sida innehåller fina bilder</h2>
    <nav>
    </nav>
</header>

<script>

let image = "https://picsum.photos/id/70/367/267"
let photo = "https://picsum.photos/id/88/367/267"
let picture = "https://picsum.photos/id/93/367/267"

</script>


<section class="photos">

<div class="image-wrapper">
    <img src={image} alt="Flexbox egenskaper">
</div>
<div class="image-wrapper">

    <img src={photo} alt="Flexbox egenskaper">
</div>
<div class="image-wrapper">

    <img src={picture} alt="Flexbox egenskaper">
</div>

</section>

<style>

    .photos{
        display: flex;
        width: 80vw;
        height: 330px;
        flex-wrap: wrap;
        background-color: gainsboro;
        border-radius: 20px;
        border: 2px solid rgb(94, 94, 94);
    }
    .image-wrapper img{ width: 100%; 
    height: 100%;}
    .image-wrapper{
        flex:1;
        height: 300px;
        margin:10px;
        border-radius: 20px;
        overflow: hidden;
        border: 2px solid black;
        box-shadow:4px 8px 10px rgba(0,0,0,0.2);
    }

    .image-wrapper:hover {flex-grow:2;}

    .image-wrapper:active {transform: scale(0.9);}

    h1{
        text-align: center;
        font-size: 75px;
        margin: 20px;
        color: gray;
    }
</style>