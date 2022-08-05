<script>
import PostForm from "./PostForm.svelte";



    export let type;


    let type_push;


    let keywords = [];
    let groups = [];

    let keyword = {name: "", tag: ""};
    let group = {name : "", tag: ""};


    let groupNameTagWords = ""
    let groupNameTag  = ""


    document.addEventListener('keydown', function(e){
        if(e.keyCode === 13){
           handlePush(type_push)
        }
    })



    function handleRemoveSelfItem(event, type){
           type == keywords ? 
            (
                keywords.splice(event, 1),
                keywords = keywords 
            ):

           groups.splice(event, 1)
           groups = groups
             
    }

    function handlePush(type){

        if(type == keyword && keyword.name !== ""){

            keywords = [...keywords, [keyword.name, keyword.tag]]
            keyword.name = ""

        }else if(type == group && group.name !== ""){

            groups = [...groups, [group.name, group.tag]]
            group.name = ""

        }
    }

    function handleInput(event, type){
        type.name = event.target.value     
        type_push = type   
    }


    function handleGroup(event){
        groupNameTag = event.target.value
        group.tag = groupNameTag
        console.log(groupNameTag)
    }


    function handleGroupWords(event){
        groupNameTagWords = event.target.value
        keyword.tag = groupNameTagWords
        console.log(groupNameTag)
    }


</script>
   

<main>


    {#if type == 'keywords' }

        <h3>Add {type}</h3>
        <div class="inputs">
            <input placeholder={type} bind:value={keyword.name} on:input={handleInput(event, keyword)} type="text">
            <input placeholder="Node" value={groupNameTagWords} on:input={handleGroupWords} type="text">
        </div>
        <button on:click={handlePush(keyword)} class="btn-add">ADD (Enter)</button>

        <div>

            {#each keywords as item, index}

                <div class="wrap-item">
                    <p>{item[0]}</p>
                    <span>Node: {item[1]}</span>
                    <button on:click={() => handleRemoveSelfItem(index, keywords)} class="remove-self-btn">X</button>
                </div>

            {/each} 
    
        </div>

    {/if}
    

    {#if type == 'groups'}

        <h3>Add {type}</h3>
        <div class="inputs">
            <input placeholder="Group Name" bind:value={group.name} on:input={handleInput(event, group)} type="text">
            <input placeholder="Node" value={groupNameTag} on:input={handleGroup} type="text">
        </div>

        <button on:click={handlePush(group)} class="btn-add">ADD (Enter)</button>

        <div>

            {#each groups as item, index}
                <div class="wrap-item">
                    <p>{item[0]}</p>
                    <span>Node: {item[1]}</span>
                    <button on:click={() => handleRemoveSelfItem(index, groups.Object)} class="remove-self-btn">X</button>
                </div>
            {/each} 

        </div>
    {/if}


   
    
</main>
    
<style>

    .btn-add{
        background-color: rgb(65, 66, 65);
        border: none;
        width: 100%;
        color: whitesmoke;
    }

    .remove-self-btn{
        background-color: rgb(235, 77, 77);
        border-radius: 3px;
        padding: 5px 20px;
        border: none;
        color: whitesmoke;
        height: 40px;
    }

    .inputs{
        display: flex;
        flex-direction: column;
        width: 25vw;
    }





    .wrap-item{
        display: flex;
        align-items: center;
        gap: 10px;
    }

    p{
        font-size: 22px;
        width: 80%;
    }

</style>