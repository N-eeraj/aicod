<script lang="ts">
  import Counter from "./components/Counter/index.svelte"
  import Container from "./components/Counter/Container.svelte"
  import Completed from "./components/Completed.svelte"
  import Sfx from "./components/Sfx.svelte"
  import Footer from "./components/Footer.svelte"

  if (window.location.href !== import.meta.env.VITE_OG_URL) {
    window.location.href = import.meta.env.VITE_OG_URL
  }

  const startTime = import.meta.env.VITE_START_DATETIME
  const duration = import.meta.env.VITE_DURATION_HOURS

  let now = $state(new Date().getTime())
  const startTimestamp = new Date(startTime).getTime()
  const endTimestamp = startTimestamp + duration * 3600000

  const hasStarted = $derived(Boolean(startTimestamp - now < 0))
  const hasEnded = $derived(Boolean(endTimestamp - now < 0))

  navigator.wakeLock.request("screen")

  setInterval(() => {
    now += 1000
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

    <Sfx />

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
