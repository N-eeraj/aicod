<script lang="ts">
  const WINNERS = [
    "SQUAD 1",
    "SQUAD 2",
    "SQUAD 3",
  ]
</script>

<main>
  {#if WINNERS.length}
    <div class="flex md:grid flex-col md:grid-cols-3 md:items-end md:gap-x-4 lg:gap-x-6 gap-y-7 md:gap-y-10">
      {#each WINNERS as winner, i}
        <div class={`flex flex-col items-center ${i === 0 && "md:order-1 md:pb-24 lg:pb-32"} ${i === 1 && "md:translate-x-1/4"} ${i === 2 && "md:order-2 md:-translate-x-1/4"}`}>
          <span class="text-xl">
            {i + 1} position
          </span>
          <h2 class={`text-primary leading-none font-digit ${i === 0 ? "text-5xl md:text-6xl lg:text-7xl" :  "text-4xl md:text-5xl lg:text-6xl"}`}>
            {winner}
          </h2>
        </div>
      {/each}
    </div>
  {:else}
    <div class="font-digit text-4xl sm:text-5xl md:text-7xl lg:text-8xl xl:text-9xl text-primary">
      THANK YOU
    </div>
  {/if}
</main>
