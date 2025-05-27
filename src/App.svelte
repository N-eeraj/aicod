<script lang="ts">
  import StartsIn from "./components/StartsIn.svelte"
  import EndsIn from "./components/EndsIn.svelte"
  import Completed from "./components/Completed.svelte"
  import Footer from "./components/Footer.svelte"

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
    <StartsIn
      now={now}
      startTimestamp={startTimestamp} />
  {:else if !hasEnded}
    <EndsIn
      now={now}
      endTimestamp={endTimestamp} />
  {:else}
    <Completed />
  {/if}
  <Footer />
</main>
