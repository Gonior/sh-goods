<script lang="ts">
    import {page} from '$app/stores'
	import type { IconName } from "$types";
    import Icon from "./Icon.svelte";
    interface Menu {
        link : string,
        icon : IconName
    }
    let menus: Menu[] = [
        {
            
            link : '/',
            icon : "home",
            
        },
        {
            
            link : '/search',
            icon : "search",
            
        },
        {
            
            link : '/items',
            icon : "cube",
            
        },
        {
            
            link : '/setting',
            icon : "cog-8-tooth",
            
        },
    ]
    
    // const handleclick = (id : number) => {
    //     menus = [...menus.map((menu) => {
    //         if(menu.id === id) menu.selected = true
    //         else menu.selected = false
    //         return menu
    //     })]
    // }
</script>
<div class="flex w-full justify-around rounded-t-xl py-3 flex-0 bg-gray-100 dark:bg-gray-900">
    {#each menus as menu}
        <div class="flex flex-col items-center justify-center">
            <a href={menu.link} class:active={$page.url.pathname === menu.link} class="button">
                <Icon name={menu.icon} class="h-8 w-8" ></Icon>
            </a>
            <div class="{$page.url.pathname === menu.link ? 'scale-100' : 'scale-0'} h-2 w-2 bg-amber-600 rounded-full transform transition-transform duration-200 ease-in-out"></div>
        </div>
        
    {/each}
    
</div>

<style>
    .button {
        @apply btn text-gray-400 dark:text-gray-600 transition-colors duration-300;
    }
    .button.active {
        @apply text-amber-600;
    }
</style>