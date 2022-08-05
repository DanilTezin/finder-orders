<script>
import ListForm from "./ListForm.svelte";
import PostForm from "./PostForm.svelte";


</script>

<main>
    <div class="wrap-content-post">
        <PostForm/>
    </div>

    <div class="wrap-content">
        <ListForm type='keywords'/>
        <ListForm type='groups'/>
    </div>
    
</main>


<style>

    .wrap-content{
        display: flex;
        justify-content: center;
        gap: 25px;
    }
    .wrap-content-post{
        display: flex;
        justify-content: flex-start;
        gap: 25px;
    }
    main{
        margin-top: 100px;
        width: fit-content;
    }

</style>