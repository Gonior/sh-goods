<script lang="ts">
    import type { IconName } from '$types'
    import Icons from "$utils/icons";

    export let name: IconName  = "icon"
    export let stroke = 1.5

</script>

<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width={stroke} stroke="currentColor" class={`h-8 w-8 ${$$props.class}`}>
    {@html Icons.find(icon => icon.name === name)?.path}
</svg>


  