<script lang="ts">
  let {
    counter,
    label,
  } = $props()
</script>

<div class="flex flex-col items-center">
  <strong class="text-primary">
    {String(counter).padStart(2, "0")}
  </strong>
  <span class="text-lg">
    {label}
  </span>
</div>
