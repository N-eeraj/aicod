<script lang="ts">
  import Container from "./Counter/Container.svelte"
  import Counter from "./Counter/index.svelte"

  let {
    now,
    endTimestamp,
  } = $props()
</script>

<Container title="Ends In">
  <Counter
    end={endTimestamp}
    start={now} />
</Container>
