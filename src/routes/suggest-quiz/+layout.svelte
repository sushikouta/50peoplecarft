<script>
    import "../../app.css";

	import "@fortawesome/fontawesome-free/css/all.min.css";
</script>

<svelte:head>
	<title>参加勢サジェストクイズ</title>
</svelte:head>

<div class="bg-amber-400 h-screen">
	<div class="bg-white fixed top-0 left-0 w-full h-10" />

	<main class="absolute top-2/4 left-2/4 translate-x-[-50%] translate-y-[-50%] text-center">
		<slot />
	</main>

	<div class="bg-white fixed bottom-0 left-0 w-full h-10" />
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=RocknRoll+One&display=swap');

	* {
		font-family: "RocknRoll One", sans-serif;
	}
</style>