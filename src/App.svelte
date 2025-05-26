<script lang="ts">
  import Counter from "./Counter.svelte"

  const startTime = import.meta.env.VITE_START_DATETIME
  const duration = import.meta.env.VITE_DURATION_HOURS

  let now = $state(new Date().getTime())
  const startTimestamp = new Date(startTime).getTime()
  const endTimestamp = startTimestamp + duration * 3600000

  const hasStarted = $derived(Boolean(startTimestamp - now < 0))
  const hasEnded = $derived(Boolean(endTimestamp - now < 0))

  setInterval(() => {
    now += 1000
  }, 1000)
</script>

<main class="flex justify-center items-center h-svh">
{#if !hasStarted}
	<p>
    Starts in
    <Counter
      end={startTimestamp}
      start={now} />
  </p>
{:else if !hasEnded}
	<p>
    Ends in
    <Counter
      end={endTimestamp}
      start={now} />
  </p>
{:else}
  <p>
    Done
  </p>
{/if}
</main>
