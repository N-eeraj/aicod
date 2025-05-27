<script lang="ts">
  let { title, children } = $props()
</script>

<div class="flex flex-col">
  {title}
  {@render children()}
</div>
