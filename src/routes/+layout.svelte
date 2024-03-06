<script lang="ts">
	// import type { LayoutData } from './$types';
	import { Toaster } from 'svelte-french-toast';
	import '../app.css';

	// export let data: LayoutData;
</script>

<Toaster />

<div class="bg-gray-50 dark:bg-gray-800 h-screen overflow-hidden disable-scrollbars select-none safe-top safe-left safe-right safe-bottom flex flex-col">
    <slot/>
</div>
