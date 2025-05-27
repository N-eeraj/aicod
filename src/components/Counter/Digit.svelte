<script lang="ts">
  let {
    counter,
    label,
  } = $props()
</script>

<div class="flex flex-col items-center gap-y-2">
  <strong class="text-primary font-digit">
    {String(counter).padStart(2, "0")}
  </strong>
  <span class="text-lg md:text-3xl">
    {label}
  </span>
</div>
