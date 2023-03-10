<script>
	let cloth, fileinput;
	const onFileSelected = (event) => {
		let image = event.target.files[0];
		let reader = new FileReader();
		reader.readAsDataURL(image);
		reader.onload = (event) => {
			cloth = event.target.result;
		};
	};
</script>

<h1>Service Page</h1>
<div id="app">
	<h1>Upload Image</h1>
	{#if cloth}
		<img class="cloth" src={cloth} alt="" />
	{:else}
		<img
			class="cloth"
			src="https://cdn4.iconfinder.com/data/icons/small-n-flat/24/user-alt-512.png"
			alt=""
		/>
	{/if}
	<img
		class="upload"
		src="https://static.thenounproject.com/png/625182-200.png"
		alt=""
		on:click={() => {
			fileinput.click();
		}}
		on:keydown={() => {
			console.log('keydown');
		}}
		on:keyup={() => {
			console.log('keyup');
		}}
	/>
	<div
		class="chan"
		on:click={() => {
			fileinput.click();
		}}
		on:keydown={() => {
			console.log('keydown');
		}}
		on:keyup={() => {
			console.log('keyup');
		}}
	>
		Choose Image
	</div>
	<input
		style="display:none"
		type="file"
		accept=".jpg, .jpeg, .png"
		on:change={(e) => onFileSelected(e)}
		bind:this={fileinput}
	/>
</div>

<style>
	#app {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-flow: column;
	}

	.upload {
		display: flex;
		height: 50px;
		width: 50px;
		cursor: pointer;
	}
	.cloth {
		display: flex;
		height: 200px;
		width: 200px;
	}
</style>
