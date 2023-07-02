<!-- Component: <script> <html> <style> -->

<script>
	import Face from './Face.svelte';
  import Container from './Container.svelte';
  import Header from './Header.svelte';
  import Buttons from './Buttons.svelte';
  import story from './story';
    
	//state
  let showHeader = false;
  let happyScore = 0;
  let storyIndex = 0;
	let name = '';

	//reactivity => re-render and update UI when any variable change
	$: question = story[storyIndex];
  $: smileySays = question.end ? finalMessage() : question.smileySays;
  $: buttons = question.buttons;
	$: if (happyScore > 0 && storyIndex === 3) showHeader = true;

  function clickHandler(e) {
		//e.detail.{...} => child component dispatch the value to event, kinda like Redux toolkit way
		if (e.detail.value === 'reset') {
			storyIndex = 0;
			happyScore = 0;
			showHeader = false;
		} else {
			storyIndex += 1;
			happyScore += e.detail.value;
		}
  }

	function finalMessage() {
		if (happyScore > 0) {
			return question.end.nice;
		}
		if (happyScore < 0) {
			return question.end.mean;
		} 
		return question.end.neutral;	
	}
</script>


<!-- Component -->
{#if showHeader} 
	<!-- if statement syntax "{:if}" => else if -->
  <Header />
{/if}
<Container>
	<!-- two way binding -->
  <input type="text" bind:value={name} placeholder="What's your name?">
  <h1>{name}, {smileySays}</h1>
  <Face {happyScore} size={storyIndex + 1} />
	<!-- event syntax -->
  <Buttons {buttons} on:click={clickHandler} />
</Container>


<!-- Styling in same file -->
<style>
	/* way to make global css rule */
	:global(*) {
		box-sizing: border-box;
	}
	:global(body, html) {
		margin: 0;
		height: 100vh;
		overflow: hidden;
		text-align: center;
	}

	/* scope only this component */
  h1 {
		font-size: 2em;
	  color: white;
		text-align: center;
    padding: 0.3em .6em;
		background: #ff3e00;
		border-radius: 50px;
	}
	input {
		width: 300px;
		font-size: 2em;
		font-family: 'Nunito', sans-serif;
		text-align: center;
		outline: 0;
		margin: 1em;
		background: transparent;
		border: 0;
		border-bottom: 1px solid black;
  }
</style>