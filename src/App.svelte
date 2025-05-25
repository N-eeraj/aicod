<script lang="ts">
const startTime = import.meta.env.VITE_START_DATETIME
const duration = import.meta.env.VITE_DURATION_HOURS

let now = $state(new Date().getTime())
const startTimestamp = new Date(startTime).getTime()
const endTimestamp = startTimestamp + duration * 3600000

setInterval(() => {
  now += 1000
}, 1000)

const timeToStart = $derived.by(() => {
  return startTimestamp - now
})
const timeToEnd = $derived.by(() => {
  return endTimestamp - now
})
</script>

<main>
{#if timeToStart > 0}
	<p>
    {timeToStart}
  </p>
{:else}
	<p>
    {timeToEnd}
  </p>
{/if}
</main>
