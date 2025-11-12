<script>
	import { onMount } from 'svelte';
	
	let isScrolled = $state(false);
	let isMobileMenuOpen = $state(false);
	
	const navItems = [
		{ path: '#home', name: 'HOME' },
		{ path: '#about', name: 'ABOUT' },
		{ path: '#services', name: 'SERVICES' },
		{ path: '#projects', name: 'PROJECTS' },
		{ path: '#contact', name: 'CONTACT' }
	];
	
	onMount(() => {
		const handleScroll = () => {
			isScrolled = window.scrollY > 100;
		};
		
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
	
	function toggleMenu() {
		isMobileMenuOpen = !isMobileMenuOpen;
	}
	
	function closeMenu() {
		isMobileMenuOpen = false;
	}
</script>

<nav class="fixed top-0 left-0 right-0 w-full z-50 transition-all {isScrolled ? 'bg-dark/95 backdrop-blur-md shadow-lg' : 'bg-dark/80 backdrop-blur-sm'} border-b border-gray-800">
	<div class="max-w-7xl mx-auto px-6 py-4">
		<div class="flex justify-between items-center w-full">
			<!-- Logo -->
			<a href="/" class="flex items-center gap-3 hover:scale-105 transition-transform group">
				<div class="w-10 h-10 border-2 border-neon rounded-lg flex items-center justify-center font-bold">
					<span class="text-xl font-mono text-neon">&lt;/&gt;</span>
				</div>
				<span class="text-white font-bold text-xl tracking-tight hidden lg:block group-hover:text-neon transition-colors">
					Afis<span class="text-neon">Dev</span>
				</span>
			</a>
			
			<!-- Desktop Menu - Always visible for testing -->
			<div class="flex gap-8 items-center">
				{#each navItems as item}
					<a href={item.path} class="text-white hover:text-neon transition-colors font-semibold text-sm tracking-wide uppercase">
						{item.name}
					</a>
				{/each}
			</div>
			
			<!-- Mobile Menu Button -->
			<button onclick={toggleMenu} class="md:hidden text-white text-2xl z-10">
				{isMobileMenuOpen ? '✕' : '☰'}
			</button>
		</div>
	</div>
	
	{#if isMobileMenuOpen}
		<div class="md:hidden absolute top-full left-0 right-0 bg-dark border-b border-gray-800">
			<div class="flex flex-col p-6 space-y-4">
				{#each navItems as item}
					<a href={item.path} onclick={closeMenu} class="text-white hover:text-neon transition-colors font-semibold text-sm tracking-wide">
						{item.name}
					</a>
				{/each}
			</div>
		</div>
	{/if}
</nav>