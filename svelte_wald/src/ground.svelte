<script>
    import Tree from './tree.svelte';
    import Lake from './lake.svelte';
    export let w;
    export let h;
    export let treeCount;
    export let lakeCount;

    let trees = [];

    let lakes = [];

    for (let i = 0; i < lakeCount; i++) {
        lakes.push({
            left: Math.random() * w,
            top: Math.random() * h,
            size: Math.random() * (100 - 5) + 5, // random size between 5 and 50
        });
    }

    for (let i = 0; i < treeCount; i++) {
        let newTree;
        do {
            newTree = {
                left: Math.random() * w,
                top: Math.random() * h,
                size: Math.random() * (50 - 5) + 5, // random size between 5 and 50
            };
        } while (isTreeNearLake(newTree, lakes, 0));

        trees.push(newTree);
    }

    function isTreeNearLake(tree, lakes, distance) {
        for (const lake of lakes) {
            const distanceToLake = Math.hypot(tree.left - lake.left, tree.top - lake.top);
            if (distanceToLake < distance + lake.size) {
                return true;
            }
        }
        return false;
    }
</script>

<div class="ground" style="width: {w}px; height: {h}px;">
    {#each lakes as lake}
        <Lake left={lake.left} top={lake.top} size={lake.size} />
    {/each}
    {#each trees as tree}
        <Tree left={tree.left} top={tree.top} size={tree.size} />
    {/each}
</div>

<style>
    .ground {
        position: relative;
        padding-right: 50px;
        padding-bottom: 50px;
        background-color: rgb(208, 184, 159);
        border-radius: 10px;
    }
</style>
