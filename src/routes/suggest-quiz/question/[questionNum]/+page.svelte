<script lang="ts">
    import Suggestion from "$lib/Suggestion.svelte";

    export let data

    let visibles = Array.from(new Array(data.question.keywords.length), (_, i) => !!(i == 0));
    function showAll() {
        for (let n = 0;n != visibles.length;n++) {
            visibles[n] = true
        }
    }

    let checked = false
    let answer = "とある参加勢"
    function checkAnswer() {
        answer = data.question.sankazei
        checked = true
    }

    function toNext() {
        if (data.num == 12) {
            location.href = "/suggest-quiz/omake"
        } else {
            location.href = "/suggest-quiz/question/" + (data.num + 1)
        }
    }
</script>

<div class="inline-flex mb-5">
    <h1 class="bg-white px-4 py-3 text-4xl">第{data.num}問目</h1>
    <h2 class="text-2xl ml-5 my-auto">この参加勢は誰でしょう？！</h2>
</div>

<h3 class="text-xl underline mb-7">{data.question.message}</h3>

<div class="inline-block">
    <table class="bg-white p-2 rounded-xl border-separate border-spacing-x-3 border-spacing-y-2 min-w-[32rem] mb-6">
        <tr>
            <td class="text-left"><i class="fa-solid fa-magnifying-glass fa-xl"></i></td>
            <td class="text-left"><span class="text-2xl">{answer}</span></td>
        </tr>
        {#each data.question.keywords as keyword, index}
            <Suggestion {answer} keyword={keyword} visible={visibles[index]} />
        {/each}
    </table>
    <div class="flex">
        <button class="block bg-blue-500 px-3 py-2 text-white text-xl hover:bg-blue-600 duration-150" on:click={showAll}>すべて表示</button>
    
        {#if checked}
            <button class="block bg-rose-500 px-3 py-2 text-white text-xl ml-auto hover:bg-rose-600 duration-150" on:click={toNext}>次の問題へ</button>
        {:else}
            <button class="block bg-blue-500 px-3 py-2 text-white text-xl ml-auto hover:bg-blue-600 duration-150" on:click={checkAnswer}>答え合わせ</button>
        {/if}
    </div>
</div>

<div class="absolute bottom-[-8rem] right-0">
    <p class="text-amber-600"></p>
</div>