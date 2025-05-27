<script lang="ts">
  let { title, children } = $props()
</script>

<div class="flex flex-col items-center gap-y-3 md:gap-y-4">
  <strong class="text-xl md:text-4xl">
    {title.toUpperCase()}
  </strong>
  {@render children()}
</div>
