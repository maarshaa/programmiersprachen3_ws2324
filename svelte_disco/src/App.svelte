<script>
	import Dancefloor from "./dancefloor.svelte";
  import Lamp from "./lamp.svelte";
</script>

<main>
  <Dancefloor w={400} h={400} lampCount={1}/>
  <Dancefloor w={200} h={200} lampCount={20}/>
  <Dancefloor w={100} h={100} lampCount={5}/>
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
