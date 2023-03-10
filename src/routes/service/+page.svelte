<script>
	let cloth, fileinput, diffusionPromise, generatedImage, diffusionExecuted;
	const onFileSelected = (event) => {
		diffusionExecuted = false;
		let image = event.target.files[0];
		let reader = new FileReader();
		reader.readAsDataURL(image);
		reader.onload = (event) => {
			cloth = event.target.result;
		};
	};

	// async function getRandomNumber() {
	// 	const res = await fetch(`https://svelte.dev/tutorial/random-number`);
	// 	const text = await res.text();

	// 	if (res.ok) {
	// 		return text;
	// 	} else {
	// 		throw new Error(text);
	// 	}
	// }

	async function download() {}

	async function getGeneratedImage(image_file) {
		// const response = await fetch();
		// const generatedImage = await response.image();
		generatedImage = image_file;

		if (true) {
			return generatedImage;
		} else {
			throw new Error('Cloth Diffusion API failed');
		}
	}

	const onButtonClicked = (event) => {
		// TODO 1 : send Generative API request
		diffusionExecuted = true;
		diffusionPromise = getGeneratedImage(cloth);
		// diffusionPromise = getRandomNumber();
		// TODO 2 : after API response, display generated Images
	};
</script>

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

	{#if cloth}
		<h1>Generated Image</h1>
		<div class="button-container">
			<button on:click={onButtonClicked}>Generate AI Image</button>
		</div>
	{/if}
	{#if diffusionExecuted}
		<div>
			{#await diffusionPromise}
				<p>Waiting Diffusion Processing...</p>
			{:then generatedImage}
				<img class="cloth" src={generatedImage} alt=""/>
				<div class="button-container">
					<button on:click={download}>Download</button>
				</div>
			{:catch error}
				<p style="color: red">{error.message}</p>
			{/await}
		</div>
	{/if}
</div>
<input
	style="display:none"
	type="file"
	accept=".jpg, .jpeg, .png"
	on:change={(e) => onFileSelected(e)}
	bind:this={fileinput}
/>

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
	.button-container {
		/* position: relative; */
		/* top: 0;
		left: 0; */
		/* width: 100vw; */
		/* height: 100vh;  */
    margin: 4px;
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		align-items: center;
		font-family: sans-serif;
	}

  .button-container > button {
        width: 128px;
        height: 48px;
        background-color: black;
        color: white;
        font-weight: bold;
        border: none;
    }

    .button-container > button:hover {
        background-color: white;
        color: black;
        outline: black solid 2px;
    }
</style>
