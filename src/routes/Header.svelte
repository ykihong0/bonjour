<header class="header">
	<div class="contents">
		<div>Logo Image</div>

		<nav class="navigation">
			<ul>
				<li><a href="/">Home</a></li>
        <li><a href="/login">Login</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/help">Help</a></li>
        <li><a href="/product">Product</a></li>
        <li><a href="/service">Service</a></li>
			</ul>
		</nav>
	</div>
</header>

<style>
	.header {
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		height: 80px;
		background-color: #dde0ea;
	}

	.contents {
		display: flex;
		width: 96%;
		max-width: 1100px;
		height: 100%;
		margin: 0 auto;
		align-items: center;
		justify-content: space-between;
	}
	.navigation ul {
		display: flex;
		list-style: none;
	}
	.navigation ul li + li {
		margin-left: 30px;
	}
</style>
