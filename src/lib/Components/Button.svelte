<script>
    export let bgColor01 = 'variant-filled-primary'
    export let bgColor02 = 'variant-filled-secondary'
    export let isTrue = true
</script>



{#if isTrue}
    <button class="btn rounded-full {bgColor01} m-4 p-4 px-6">Click Me!</button>
{:else}
    <button class="btn rounded-full {bgColor02} m-4 p-4 px-6">Click Me!</button>
{/if}

<button class="btn variant-outline-primary" on:click={() => isTrue = !isTrue}>
    Toggle Condition
</button>