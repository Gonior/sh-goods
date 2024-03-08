<script lang="ts">
    import Icon from "$components/Icon.svelte";
	import Modal from "$components/modal.svelte";
    
	
	
    
    let openModal = false
    
</script>

<h1>home</h1>
    <!-- <header>
        this is header
    </header> -->
    <!-- <slot /> -->
    <!-- <main class="flex-1 overflow-y-auto px-2 font-medium">
        
        
        <div>
            <button class="btn-primary"  on:click={() => openModal = !openModal}>Open Modal</button>
            <button class="btn-secondary" on:click={() => openPopover() }>
                Toogle Toast
            </button>
            <button class="btn-secondary" disabled={true} on:click={() => openModal = !openModal}>Open Modal</button>
            
            <Modal bind:show={openModal}>
                <div class="space-y-2">
                    <h1 class="text-2xl font-bold">Hello World!</h1>
                    <p>I'm a stylized modal.</p>
                </div>
            </Modal>
        </div>
        darkmode {isDarkMode} open modal {openModal}
        primary : amber-600
            background : gray-50 dark:gray-800
            secondary : gray-300 dark:gray-700
            content : gray-800 dark:text-white
            subcontent : gray-500 dark:gray-400
            disabled : opacity-50 [bg, text]
    </main> -->