<script>
  export let text = "ACET";

  // turn text into array of characters
  const letters = text.split("");
</script>

<style>
  .letter {
    transition: color 0.25s ease, transform 0.25s ease, opacity 0.25s ease;
    display: inline-block;
    cursor: pointer;
  }

  .hover-container:hover .letter {
    opacity: 0.2;
  }

  .letter:hover {
    opacity: 1 !important;
    color: #a78bfa; /* violet-400 */
    transform: translateY(-6px);
  }
</style>

<div class="hover-container text-7xl font-extrabold text-white tracking-wider">
  {#each letters as char, i}
    <span
      class="letter"
      style="transition-delay: {i * 40}ms"
    >
      {char}
    </span>
  {/each}
</div>
