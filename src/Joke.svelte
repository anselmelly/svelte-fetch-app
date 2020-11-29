<script>
    export let joke = {};

    console.log(joke);
</script>

{#if joke.id !== undefined}
    <div class="flex flex-grow">
        <div class="bg-gray-700 w-full flex-1 rounded-md p-5 text-white">
            <div class="flex flex-row justify-between">
                <p class="flex-grow">{joke.setup}</p>
                <p class="rounded-full bg-gray-500 px-5 h-8 items-center text-gray-300">{joke.type}</p>
            </div>
            <p class="italic font-semibold">{joke.punchline}</p>
        </div>
    </div>
{/if}
