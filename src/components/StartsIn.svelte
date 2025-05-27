<script lang="ts">
  import Container from "./Counter/Container.svelte"
  import Counter from "./Counter/index.svelte"

  let {
    now,
    startTimestamp,
  } = $props()
</script>

<Container title="ENDS IN">
  <Counter
    end={startTimestamp}
    start={now} />
</Container>
