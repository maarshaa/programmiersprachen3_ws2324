<script>
  import Ground from "./ground.svelte";
</script>

<main>
  <Ground
    w={Math.floor(Math.random() * 1000) + 500}
    h={Math.floor(Math.random() * 500) + 200}
    treeCount={Math.floor(Math.random() * 800) + 200}
    lakeCount={Math.floor(Math.random() * 3) + 3} />
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
