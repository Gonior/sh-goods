<script lang="ts">
    import Icon from "$components/Icon.svelte";
    
    const getItems = async (userId: string) => {
        
        let responses = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${userId}`)
        let json = await responses.json()
        // console.log(json)    
        if(responses.ok) {
            return json
        } else throw new Error('Gangguan pada server')
        
        
    }
    const handleSearch = () => {
       
        promise = getItems(keyword)
        // console.log(promise)
    }
    let keyword = ""
    let promise: Promise<any>
</script>
<div class="flex flex-col">
    <div class="relative">
        <input type="text" on:keyup={handleSearch} bind:value={keyword} class="py-2 px-10 rounded-lg w-full dark:bg-gray-700 focus:ring-offset-transparent focus:ring-1 focus:ring-offset-2 focus:ring-amber-600 outline-none" placeholder="Cari..">
        <div class="absolute top-1 left-1.5">
            <Icon name="search" class="h-6 w-6 text-gray-500 dark:text-gray-300 " />
        </div>
        <button class="absolute top-1 right-1.5 btn !p-0" on:click={() => keyword = ''}>
            <Icon name="close" class="h-6 w-6 text-gray-400 dark:text-gray-500" />
        </button>
    </div>
    <div class="mt-5 space-y-2 flex-1 overflow-y-auto max-h-[82dvh]">
        {#if keyword}
        {#await promise}
            <p class="px-10 text-gray-400">memuat..</p>
            {:then data}
                {#if data}
                    {#each data as d}
                        <a href="/" class="flex items-center">
                            <div class="pl-1.5">
                                <Icon name="cube" class="h-6 w-6 text-gray-400 dark:text-gray-500 " />
                            </div>
                            <p class="pl-3 flex-1 truncate max-w-prose">{d.title}</p>
                        </a>
                    {:else}
                        <p class="px-10 text-gray-400">Tidak ditemukan <span class="text-gray-800 dark:text-white">{keyword}</span></p>
                    {/each}
                {/if}
            {:catch error}
            <p class="text-red-500">{error.message}</p>
            {/await}
            
        {/if}
    </div>

</div>