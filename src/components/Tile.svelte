<script>
    import { createEventDispatcher } from "svelte";
    import runGameStore from "../stores/GameRunsStore";

    export let tile;

    const dispatch = createEventDispatcher();

    function tileClicked(e) {
        let isActive = e.srcElement.classList.contains('active');

        dispatch('activeTileClicked', isActive);
    }
</script>

{#if ($runGameStore.run === true)}
<div class={tile.active ? 'tile active' : 'tile'} on:click={tileClicked}></div>
{:else}
<div class={tile.active ? 'tile active' : 'tile'}></div>
{/if}
<style>
    .tile {
        height: 10em;
        width: 10em;
        background: rgb(32, 32, 32);
        border-radius: 5px;
        margin: 2em;
    }
    .active {
        background: red;
    }
</style>
