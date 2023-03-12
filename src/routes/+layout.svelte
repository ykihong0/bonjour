<!-- <nav>
	<a href="/">Home</a>
  <a href="/login">Login</a>
	<a href="/about">About</a>
	<a href="/help">Help</a>
	<a href="/product">Product</a>
	<a href="/service">Service</a>
</nav>
<slot />

<style>
	nav {
		display: block;
	}
</style> -->
<script>
	import Header from './Header.svelte';
	import Footer from './Footer.svelte';
</script>

<div class="layout">
	<Header />
	<main class="main">
		<slot />
	</main>
	<Footer />
</div>

<style>
	.layout {
		padding-top: 80px;
	}

	.main {
		min-height: calc(100vh - 180px);
	}
</style>
