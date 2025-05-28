<script lang="ts">
  const ticking = new Audio("/sfx/tick.mp3")
  ticking.loop = true
  let isTicking = false

  function toggleSound() {
    if (isTicking) {
      ticking.pause()
    } else {
      ticking.play()
    }
    isTicking = !isTicking
  }
</script>

<button
  class="fixed top-4 right-4 size-10 p-3 bg-gray-600 rounded cursor-pointer"
  on:click={toggleSound}>
  <img
    src={`/images/${isTicking ? 'mute.png' : 'sound.png'}` }
    alt="sound-toggle"
    class="invert" />
</button>
