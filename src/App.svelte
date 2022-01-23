<script lang="ts">
	import Links from "./Links.svelte";
	import type { Link } from "./Links.svelte";
	import Logo from "./Logo.svelte";

	const links: Link[] = [
		{ text: "visit my website", href: "https://kristenbrookedesign.com" },
		{ text: "request a stationary quote", href: "https://docs.google.com/forms/d/e/1FAIpQLSeVh_o0DaSIS1zI5jwbbuu-EFoq7UbOvZ65qsbDcoiHfl8YcA/viewform"},
		{ text: "instagram", href: "https://www.instagram.com/kristenandcreative" },
		{ text: "email me", href: "mailto:kristen@kristenbrookedesign.com" },
	]
</script>


<main>
	<img id="avatar" src="/assets/avatar.png" alt="Avatar" />

	<h1>HELLO THERE!</h1>

	<div class="links">
		<Links links={links} />
	</div>

	<Logo />
</main>


<style>
	main {
		padding: 1rem;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	#avatar {
		height: 16rem;
		width: 16rem;
	}

	@media only screen and (max-height: 800px) {
		#avatar {
			height: 12rem;
			width: 12rem;
		}
	}

	h1 {
		font-size: 2rem;
        letter-spacing: 8px;
		font-family: 'Analogue';
		text-align: center;
    }
</style>