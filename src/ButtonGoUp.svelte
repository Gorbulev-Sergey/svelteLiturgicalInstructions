<script>
  let y = 0;
</script>

<svelte:window bind:scrollY={y} />

<button
  id="btn-back-to-top"
  class="position-fixed bottom-0 end-0 m-2 btn btn-light bg-opacity-10 text-dark"
  on:click={() => (y = 0)}><i class="fa-solid fa-arrow-up-long" /></button
>
