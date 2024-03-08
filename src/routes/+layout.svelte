<script lang="ts">
	import '../app.css';
	import { Toaster } from 'svelte-french-toast';
	import BottomNavigation from "$components/bottomNavigation.svelte";
	import { browser } from '$app/environment'

    if(browser) {
        if (localStorage.theme === "dark" || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            document.documentElement.classList.add('dark');
            localStorage.setItem('theme', 'dark')
        } else {
            document.documentElement.classList.remove('dark');
            localStorage.setItem('theme', 'light')
        }
    }
	// export let data: LayoutData;
</script>

<Toaster />

<div class="bg-gray-50 w-full dark:bg-gray-800 max-h-dvh overflow-hidden disable-scrollbars select-none safe-top safe-left safe-right safe-bottom flex justify-center items-center">
	<div class="h-dvh flex flex-col w-full max-w-screen-md">
		<main class="flex-1 overflow-y-auto p-4 font-medium ">
			<slot/>
		</main>
		<BottomNavigation/>
	</div>
</div>
