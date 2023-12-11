<script>   
import Lamp from "./lamp.svelte"; 
export let w;
export let h;
export let lampCount;

let lamps = [];

for (let i = 0; i < lampCount; i++) {
  lamps.push({
    left: Math.random() * w,
    top: Math.random() * h,
  });
}

console.log('Die erste Lampe ist bei left: ${lamps[0].left}px und top: ${lamps[0].top}px.')
</script>

<div class="dancefloor" style="width: {w}px; height: {h}px;">
{#each lamps as lamp}
  <Lamp left={lamp.left} top={lamp.top} />
{/each}
</div>

<style>
.dancefloor {
    position: relative;
  background-color: #222;
  border: 4px solid grey;
  border-radius: 10px;
}
</style>