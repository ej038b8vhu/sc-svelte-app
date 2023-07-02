<script>
    //to dispatch value to parent event handler
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();  

    //to take prop from parent
    export let buttons;  
</script>

<!-- Component -->
<div class="buttons-container">
    <!-- buttons is an array therefore have length to loop through -->
    {#each buttons as button}
        <!-- dispatch('event type', { value to pass }) -->
        <button on:click={() => dispatch('click', { value: button.value })}>
            {button.text}
        </button>
    {/each}
</div>

<style>
    .buttons-container {
        display: flex;
        flex-wrap: wrap;
        padding: 2em 1em;
    }
    button {
        color: white;
        font-size: 1.2rem;
        font-family: 'Nunito', sans-serif;
        margin: 10px;
        padding: 0.7em 1em;
        cursor: pointer;
        border: none;
        border-radius: 50px;
        background-color: #40b3ff;
	}
</style>