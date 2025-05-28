<script lang="ts">
  import Counter from "./components/Counter/index.svelte"
  import Container from "./components/Counter/Container.svelte"
  import Completed from "./components/Completed.svelte"
  import Footer from "./components/Footer.svelte"

  if (import.meta.env.VITE_OG_URL && window.location.href !== import.meta.env.VITE_OG_URL) {
    window.location.href = import.meta.env.VITE_OG_URL
  }

  const startTime = import.meta.env.VITE_START_DATETIME
  const duration = import.meta.env.VITE_DURATION_HOURS

  let now = $state(new Date().getTime())
  const startTimestamp = new Date(startTime).getTime()
  const endTimestamp = startTimestamp + duration * 3600000

  let isTicking = $state(false)
  const sfx = new Audio("/sfx/tick.mp3")

  const hasStarted = $derived(Boolean(startTimestamp - now < 0))
  const hasEnded = $derived(Boolean(endTimestamp - now < 0))

  navigator.wakeLock.request("screen")

  setInterval(() => {
    now += 1000
    if (isTicking) {
      sfx.currentTime = 0
      sfx.play()
    }
  }, 1000)
</script>

<main class="flex justify-center items-center h-svh pt-8">
  <img
    src="/images/background.gif"
    alt="matrix-rain"
    class="fixed size-full top-0 opacity-20 -z-10" />

  <img
    src="/images/logo.svg"
    alt="logo"
    class="fixed top-16 w-1/2 max-w-42" />

  <button
    class="fixed top-4 right-4 size-10 p-3 bg-gray-600 rounded cursor-pointer"
    onclick={() => isTicking = !isTicking}>
    <img
      src={`/images/${isTicking ? 'sound.png' : 'mute.png'}` }
      alt="sound-toggle"
      class="invert" />
  </button>

  {#if !hasEnded}
    <Container title={hasStarted ? "ENDS IN" : "STARTS IN"}>
      <Counter
        end={hasStarted ? endTimestamp : startTimestamp}
        start={now} />
    </Container>
  {:else}
    <Completed />
  {/if}

  <Footer />
</main>
