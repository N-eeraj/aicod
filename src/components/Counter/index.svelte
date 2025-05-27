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

<div class="flex gap-x-2 text-5xl md:text-7xl">
  <Digit
    counter={dd}
    label="Days" />
  :
  <Digit
    counter={hh}
    label="Hours" />
  :
  <Digit
    counter={mm}
    label="Minutes" />
  :
  <Digit
    counter={ss}
    label="Seconds" />
</div>
