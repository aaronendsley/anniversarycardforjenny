<script>
	import { fly, fade, scale } from 'svelte/transition';
	import jenny from '$lib/images/jenny.jpg?run&width=388&height=388&fit=cover';
	import Img from '@zerodevx/svelte-img';
	import '@fontsource/red-rose/700.css';
	import '@fontsource/open-sans/400.css';

	let timer = 0;
	const start = setInterval(() => {
		if (timer <= 3) {
			timer += 1;
		} else {
			clearInterval(start);
		}
	}, 1000);
</script>

<div class="container">
	{#if timer <= 1}
		<div class="loading"><p>Loading...</p></div>
	{/if}
	{#if timer > 2}
		<div class="titleDiv" in:fly={{ y: 200, duration: 4000 }}>
			<p>Happy &nbsp;</p>
			<p>15th &nbsp;</p>
			<p>Anniversary &nbsp;</p>
			<p>Jenny &nbsp; !</p>
		</div>
	{/if}

	{#if timer === 4}
		<div transition:scale={{ duration: 3000, delay: 500, opacity: 0, start: 0.5 }}>
			<Img class="hero-image" src={jenny} alt="A photo of jenny on our wedding day" />
		</div>
	{/if}
	{#if timer === 4}
		<div class="content" in:fade={{ duration: 5000 }}>
			<p>
				15 years ago I married my best friend. Your Still my best friend! It was the best decision I
				made. Your a great Mom! Your the best wife ever! Your my favorite Person! I love watching
				Star Trek, Big Bang Theory, The Office, and all the new movies with you! I love all our
				jokes. I love growing in Christ with you! You Are my Best Friend and I could not imagine
				life with out you! Nor would I have only been able to build this page without of all of your
				countless hours of patience and grace youve shown me as I've spent hours pouring over
				Tutorials and books. Your my greatest encourager. I love you! Happy 15th Anniversary!
			</p>
			<p>Love,</p>
			<p>-Aaron</p>
		</div>
	{/if}
</div>

<style lang="postcss">
	:global(body {
		background: #E6E6FA;
	}
   
    .hero-image {
		border: solid 3px purple;
		border-radius: 100%;
		height: 200px;
		width: 200px;
		margin: 20px auto 0 auto;
		display: flex;
	}
	.content-image{
		width:100%;
		height: fit-content;
	}
    )
    .loading p {
		color: purple;
		font-size: 1.5rem;
		text-shadow: 1px 1px 2px #89cff0, 0 0 1em #89cff0, 0 0 0.2em #89cff0;
		font-family: 'Red Rose', cursive;
	}
	.container {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.content {
		width: 70%;
		background: white;
		margin: 15px auto;
		padding: 20px;
		font-family: 'Open Sans', sans-serif;
		letter-spacing: 1px;
		border-radius: 10px;
	}

	.titleDiv {
		width: 80%;
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative;
	}

	.titleDiv p {
		margin: 0;
		padding: 0;
		color: purple;
		font-size: 1.5rem;
		text-shadow: 1px 1px 2px #89cff0, 0 0 1em #89cff0, 0 0 0.2em #89cff0;
		font-family: 'Red Rose', cursive;
	}
	.titleDiv::before {
		content: '';
		position: absolute;
		left: 0;
		top: 0;
		height: 4px;
		width: 100%;
		margin-bottom: 10px;
		border-bottom: 1px solid purple;
	}
	.titleDiv::after {
		content: '';
		position: absolute;
		right: 0;
		bottom: 0;
		height: 4px;
		width: 100%;
		border-bottom: 1px solid purple;
	}

	@media (min-width: 600px) {
		.titleDiv p {
			font-size: 3.5rem;
		}

		.content {
			width: 500px;
		}
	}
</style>
