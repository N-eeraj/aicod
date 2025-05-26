<script lang="ts">
  let { end, start } = $props()

  const timeToEnd = $derived.by(() => {
    const timeLeftMs = end - start
    let timeLeft = timeLeftMs / 1000
    const dd = String(Math.floor(timeLeft / 86400)).padStart(2, "0")
    timeLeft -= Number(dd) * 86400
    const hh = String(Math.floor(timeLeft / 3600)).padStart(2, "0")
    timeLeft -= Number(hh) * 3600
    const mm = String(Math.floor(timeLeft / 60)).padStart(2, "0")
    timeLeft -= Number(mm) * 60
    const ss = String(Math.floor(timeLeft)).padStart(2, "0")
    return { dd, hh, mm, ss }
  })
</script>

<div class="flex gap-x-0.5">
  <span>
    {timeToEnd.dd}
  </span>
  :
  <span>
    {timeToEnd.hh}
  </span>
  :
  <span>
    {timeToEnd.mm}
  </span>
  :
  <span>
    {timeToEnd.ss}
  </span>
</div>
