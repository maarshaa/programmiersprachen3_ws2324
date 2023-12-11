<script>
  import Dancefloor from "./dancefloor.svelte";
</script>

<main>
  {#each Array.from({ length: Math.floor(Math.random() * 8) + 1 }) as _, i}
    <Dancefloor
      w={Math.floor(Math.random() * 400) + 100}
      h={Math.floor(Math.random() * 400) + 100}
      lampCount={Math.floor(Math.random() * 50) + 10}
      key={i}
    />
  {/each}
</main>

<style>
  main {
    display: flex;
    gap: 10px;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
</style>
