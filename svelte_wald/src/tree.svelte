<script>
    export let left;
    export let top;
    export let size; 


    const treeImages = [
        'tree1.png',
        'tree2.png',
        'tree3.png',
        'tree4.png',
    ];

    const randomTreeImage = treeImages[Math.floor(Math.random() * treeImages.length)];

</script>

<img
    src={`/images/${randomTreeImage}`}
    alt="Tree"
    class="tree"
    style="left: {left}px; top: {top}px; width: {size}px; height: {size}px;"
/>

<style>
    .tree {
        position: absolute;
        allign-items: center;
    }
</style>
