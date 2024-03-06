<script lang="ts">
	import Popover from "$components/popover.svelte";
    import Icon from "$components/Icon.svelte";
	import Toggle from "$components/toggle.svelte";
	import Modal from "$components/modal.svelte";
    import toast from "svelte-french-toast";
    import { browser } from '$app/environment'
    let isDarkMode = false
    let openModal = false

    if(browser) {
        if (localStorage.theme === "dark" || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            document.documentElement.classList.add('dark');
            isDarkMode = true;
        } else {
            document.documentElement.classList.remove('dark');
            isDarkMode = false;
        }
    }
    const handleSwitchDarkMode = (e : CustomEvent) => {
        let checked = e.detail.checked

        localStorage.setItem('theme', checked ? 'dark' : 'light')
        checked
            ? document.documentElement.classList.add('dark')
            : document.documentElement.classList.remove('dark');
    }

    const openPopover = () => {
        let style = `font-weight : 500;${localStorage.theme === "dark" ? 'background : #374151;color:#fff' : ''}`
        toast.success("it's work!", { position: 'bottom-center', style})
    }
</script>

<header>
    this is header
</header>
<main class="flex-1 overflow-y-auto px-2 font-medium">
    
    <div class="flex items-center p-2 justify-between">
        <div class="flex items-center space-x-1">
            <h1 class="">Mode Gelap</h1>
            <Popover>
                <svelte:fragment slot="button">
                    <button class="text-gray-500 dark:text-gray-400">
                        <Icon name="information-circle"></Icon>
                    </button>
                </svelte:fragment>
                <svelte:fragment slot="content">
                    <div class="">
                        <p class="">Ubah tampilan menjadi aplikasi gelap.</p>
                    </div>
                </svelte:fragment>
            </Popover>
        </div>
        
        <Toggle bind:checked={isDarkMode} on:change={handleSwitchDarkMode}/>
    </div>
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
</main>

<footer>this is footer</footer>
