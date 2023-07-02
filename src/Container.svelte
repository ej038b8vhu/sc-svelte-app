<!-- Component -->
<div class="Container">
		<!-- use <slot> to render children -->
    <slot></slot>
</div>

<style>
	.Container {
		width: 55vw;
		height: 70vh;
		min-width: 500px;
		padding: 20px;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-around;
		border: solid  #40b3ff 20px;
		font-family: 'Nunito', sans-serif;
	}
</style>