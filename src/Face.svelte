<script>
    //use export syntax to accept prop from parent and give default value
    export let size = 1;
    export let happyScore = 1;

    const faceList = ['😄', '😡', '😭', '😭', '😕',  '😐', '😄', '😀', '😄', '😊', '😘'];

    //reactivity
    $: index = happyScore + 5;
</script>

<div style="font-size: {size}em">
    {faceList[index]}
</div>