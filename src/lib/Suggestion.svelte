<script lang="ts">
    export let answer: String
    export let keyword: String
    export let visible = false
</script>

<tr>
    <td />

    <td class="text-left">
        <span class="text-zinc-600 text-2xl">{answer}</span>
        <div class="inline-block ml-2">
            {#if visible}
                <span class="text-2xl">{keyword}</span>
            {:else}
                <button on:click={() => { visible = true }} class="mb-auto text-blue-700 underline hover:text-blue-900">クリックで表示</button>
            {/if}
        </div>
    </td>
</tr>