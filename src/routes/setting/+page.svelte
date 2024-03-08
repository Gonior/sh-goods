<script lang="ts">
    // import type { PageData } from './$types';
    import Toggle from "$components/toggle.svelte";
    import Popover from "$components/popover.svelte";
    import toast from "svelte-french-toast";
    import Icon from "$components/Icon.svelte";
	import { onMount } from "svelte";
    // export let data: PageData;

    let isDarkMode = false
    onMount(() => {
        if("theme" in localStorage && localStorage.theme === "dark") {
            isDarkMode = true
        }
    })

    const handleSwitchDarkMode = (e : CustomEvent) => {
        let checked = e.detail.checked
        localStorage.setItem('theme', checked ? 'dark' : 'light')
        checked
            ? document.documentElement.classList.add('dark')
            : document.documentElement.classList.remove('dark');
    }
    const openToast = () => {
        let style = `font-weight:500; ${localStorage.theme === "dark" ? 'background : #374151;color:#fff' : ''}`
        toast.success("it's work!", { position: 'bottom-center', style})
    }
    
</script>

<div class="flex items-center p-2 justify-between">
    <div class="flex items-center space-x-1">
        <h1 class="">Mode Gelap</h1>
        <Popover>
            <svelte:fragment slot="button">
                <button class="text-gray-500 dark:text-gray-400">
                    <Icon name="information-circle" class="h-6 w-6"></Icon>
                </button>
            </svelte:fragment>
            <svelte:fragment slot="content">
                <div class="">
                    <p class="">Ubah tampilan aplikasi menjadi gelap.</p>
                </div>
            </svelte:fragment>
        </Popover>
    </div>
    <Toggle bind:checked={isDarkMode} on:change={handleSwitchDarkMode}/>
</div>
