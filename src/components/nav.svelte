<script>
	// import dark mode toggle button
	import Dark from './dark.svelte';
</script>

<nav class="flex flex-row justify-between items-center w-full">
	<a href="/">
		<img
			class="hover:scale-105 "
			src="https://fontmeme.com/permalink/230201/187efe9a23703852ffc83845a6e0fdb1.png"
			alt="Sveltedex"
		/>
	</a>
	<div>
		<a href="/about">
			<img
				class="hover:scale-105 ml-5"
				src="https://fontmeme.com/permalink/220704/d36f0a4080e3ba35ed4da551b3b57d9a.png"
				alt="About"
			/>
		</a>
		<Dark />
	</div>
</nav>
