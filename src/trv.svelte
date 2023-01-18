<script lang="ts">
    import Data from "./assets/data.json"
    $: len = Object.keys(Data).length
    let sbmt = ' ';
    let attemps = 0;
    let level = 0;

    function onKeyPress(e){
        if(e.charCode === 13)
            attemp();
     }
    function attemp(){

                console.log(Data[level].answer)
                console.log(sbmt.trim().toLowerCase())
            if (sbmt.trim().toLowerCase() === Data[level].answer){
                console.log("winner")
                attemps=0;
                answer = Data[level].img;
                level++;
                sbmt=" "
                return
            }
            attemps++;
            sbmt=" "
            console.log("try again")
    }
    let answer = "images/emoney.png"
     
</script>

<div class="container mx-auto  w-screen h-screen flex flex-col space-y-5 justify-center items-center" >
<div class="container flex items-center justify-center">
    <img src="{answer}" alt="">
</div>
    <div class=" w-screen h-96  ">
        <div class="flex flex-row justify-around h-96   px-3 items-center space-x-5">
        
            {#if level >=  len}
                <div class="container item-center justify-center ">
                    <h1 class="text-3xl text-center text-purple-600">You win!!</h1>       
                    <h2 class="text-xl text-center p-3"><a href="https://www.youtube.com/watch?v=TaP3EK99Pfs">Click me</a></h2>
                </div>
            {:else}            
                <div class="p-3  border-4 rounded-xl border-emerald-600  w-1/3 h-72">
                    {#if attemps >= 0}
                        <img src="{Data[level].choices.ch1}" alt="" class="w-full h-full ">
                    {/if} 
                </div>  
                
                <div class="p-3  border-4 rounded-xl border-emerald-600 w-1/3 h-72">
                    {#if attemps >= 1}
                        <img src="{Data[level].choices.ch2}" alt="15" class="w-full h-full">
                    {/if} 
                </div>  
                
                <div class="p-3 border-4  rounded-xl border-emerald-600 w-1/3 h-72">
                    {#if attemps >= 2}
                        <img src="{Data[level].choices.ch3}" alt="15" class="w-full h-full">
                    {/if} 
            </div>
        {/if}
        </div> 
        </div> 
    <div class="container  flex justify-center  items-center">
        <input  on:keypress={onKeyPress} class="text-center p-1 rounded-md"  type="text" bind:value="{sbmt}" >
        <button on:input={attemp} class="px-3" >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
             <path stroke-linecap="round" stroke-linejoin="round" d="M12.75 15l3-3m0 0l-3-3m3 3h-7.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
        </button>
    </div>
</div>

<style>
</style>
