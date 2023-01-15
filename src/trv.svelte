<script lang="ts">
    import Data from "./data.json"
    $: len = Object.keys(Data).length
    let sbmt = ' ';
    let attemps = 0;
    let level = 0;
    function attemp(){

            if (sbmt.trim() === "bingo"){
                alert("heelp")
                console.log("winner")
                level++;
                attemps=0;
                return
            }
            attemps++;
            console.log("try again")
    }
</script>

<div class="container mx-auto w-screen h-screen flex flex-col space-y-3 justify-center items-center">
    <div class="border  border-purple-600 w-screen h-96">
        <h1 class="text-5xl">{attemps}{len}</h1>
        <div class="flex flex-row justify-around h-96  px-3 items-center space-x-2">
            {#if level > len }
                console.log("you won ")
                 
            {/if}            
            <div class="p-3  border border-white-600">
                {#if attemps >= 0}
                    <img src="{Data[level][0].src}" alt="111" class="w-12 h-12">
                {/if} 
            </div>  
            
            <div class="p-3  border border-white-600">
                {#if attemps >= 1}
                    <img src="{Data[level][1].src}" alt="111" class="w-12 h-12">
                {/if} 
            </div>  
            
            <div class="p-3  border border-white-600">
                {#if attemps >= 2}
                    <img src="{Data[level][2].src}" alt="111" class="w-12 h-12">
                {/if} 
            </div>
       
       </div>
    </div>
        <div class="container  flex justify-center  items-center">
        <input  class="text-center p-1"  type="text" bind:value="{sbmt}" >
        <button on:click={attemp} class="px-3">Clcik me</button>
    </div>
</div>

<style>
</style>
