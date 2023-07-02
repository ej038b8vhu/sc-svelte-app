<header>
	<!-- for loop syntax => each [times] as variable -->
  {#each [0] as _}
    <img alt="svelte logo" src="https://res.cloudinary.com/practicaldev/image/fetch/s--pf-5vyuj--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/ji7zisis4c0f4ce2cer1.png">
  {/each}
</header>

<style>
	img {
		height: 100%;
	}
  header {
		width: 100%;
		height: 240px;
		display: flex;
		justify-content: center;
		position: absolute;
		top: -1em;
		left: 8%;
	}
</style>