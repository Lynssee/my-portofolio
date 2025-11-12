<script>
	import '../app.css';
	import Navbar from '$lib/components/Navbar.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import { inject } from '@vercel/analytics';
	
	let { children } = $props();
</script>

<svelte:head>
	<title>Sulthan Hafizh Pratama - Full Stack Developer</title>
	<meta name="description" content="Full Stack Developer dengan passion dalam pengembangan aplikasi dengan Intregasi AI" />
</svelte:head>

<Navbar />
<main class="min-h-screen">
	{@render children?.()}
</main>
<Footer />