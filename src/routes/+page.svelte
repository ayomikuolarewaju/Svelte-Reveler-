<script>
    import img from './img/down-arrow.png'
    export let data;
    const product = data.products

    let rev = true
    
    const reveler =(id)=>{
        const pdi = product.filter((p)=>p.id === id)
        let i = pdi[0].id
        if(i === id){
           rev = !rev;
        }
    }

</script>



<div class="h-auto p-10 bg-gray-200">

    <div class="container mx-auto">
        {#each product as pd (pd.id)}
            {#if rev}
           <div class="flex flex-row justify-between  bg-purple-600  p-2 m-2 space-x-5 w-2/3 mx-auto">
            <h3 class=" text-2xl text-white">{pd.title}</h3>
            <img src="{img}" class="w-16 h-16 text-white" on:click={()=>{reveler(pd.id)}} alt="revelers" on:keydown={()=>{reveler(pd.id)}}>
           </div>
           <div class="hidden p-2 m-2 w-2/3 mx-auto">
            <p class="">{pd.description}</p>
           </div>
           {:else}
           <div class="flex flex-row justify-between  bg-purple-600  p-2 m-2 space-x-5 w-2/3 mx-auto">
               <h3 class="text-2xl text-white bg-purple-600">{pd.title}</h3>
               <img src="{img}" class="w-16 h-16 text-white" on:click={()=>{reveler(pd.id)}} alt="revelers" on:keydown={()=>{reveler(pd.id)}}>
          </div>
          <div class="flex p-2 m-2 w-2/3 mx-auto transition delay-1000 bg-gray-500 text-white">
            <p class="">{pd.description}</p>
          </div>
            {/if}
        {/each}
    </div>

</div>