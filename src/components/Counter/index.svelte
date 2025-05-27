<script lang="ts">
  import Digit from "./Digit.svelte"

  let { end, start } = $props()

  const { dd, hh, mm, ss } = $derived.by(() => {
    const timeLeftMs = end - start
    let timeLeft = timeLeftMs / 1000
    const dd = Math.floor(timeLeft / 86400)
    timeLeft -= Number(dd) * 86400
    const hh = Math.floor(timeLeft / 3600)
    timeLeft -= Number(hh) * 3600
    const mm = Math.floor(timeLeft / 60)
    timeLeft -= Number(mm) * 60
    const ss = Math.floor(timeLeft)
    return { dd, hh, mm, ss }
  })
</script>

<div class="flex gap-x-2 text-4xl sm:text-5xl md:text-7xl lg:text-8xl xl:text-9xl">
  <Digit
    counter={dd}
    label="DAY" />
  :
  <Digit
    counter={hh}
    label="HOURS" />
  :
  <Digit
    counter={mm}
    label="MINUTES" />
  :
  <Digit
    counter={ss}
    label="SECONDS" />
</div>
