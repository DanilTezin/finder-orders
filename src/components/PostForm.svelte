<script>



async function handleRequestPost(){
    
    await setTimeout(()=> console.log("hello"), 3000)
}



</script>

<main>
    <button on:click={handleRequestPost} class="req-btn">Request posts</button>
    <span class="">Not requested</span>
</main>

<style>

    .req-btn{
        background-color: rgb(151, 226, 155);
        border: none;
        padding: 15px 35px;
        margin: 0;
    }
    span{
        background-color: rgb(65, 66, 65);
        padding: 15px 190px;
        color: whitesmoke;
    }

    main{
        display: flex;
        align-items: center;
        margin-bottom: 20px;
    }
</style>