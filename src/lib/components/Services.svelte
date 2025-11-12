<script>
	const services = [
		{
			title: 'Web & App Development',
			description: 'Building responsive and performant web and mobile applications using modern technologies',
			icon: 'M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4'
		},
		{
			title: 'Network & Server Management',
			description: 'Managing and optimizing network infrastructure and server systems for reliable performance',
			icon: 'M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01'
		},
		{
			title: 'Business Analysis & System Design',
			description: 'Analyzing business requirements and designing scalable system architectures',
			icon: 'M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01'
		},
		{
			title: 'IT Infrastructure & Security',
			description: 'Implementing secure and robust IT infrastructure solutions to protect your systems',
			icon: 'M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z'
		},
		{
			title: 'Automation & Integration',
			description: 'Streamlining workflows and integrating systems for improved efficiency and productivity',
			icon: 'M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15'
		}
	];
</script>

<section id="services" class="py-20 px-6 bg-dark-secondary">
	<div class="max-w-7xl mx-auto">
		<h2 class="text-4xl font-bold text-center mb-12">Services</h2>
		<div class="grid md:grid-cols-3 gap-8">
			{#each services as service}
				<div class="bg-dark border border-gray-800 rounded-2xl p-8 hover:border-neon/50 transition-all group hover:-translate-y-2">
					<div class="w-16 h-16 bg-neon/10 border-2 border-neon rounded-lg flex items-center justify-center mb-6 group-hover:bg-neon transition-colors">
						<svg class="w-8 h-8 text-neon group-hover:text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={service.icon}></path>
						</svg>
					</div>
					<h3 class="text-xl font-bold mb-4">{service.title}</h3>
					<p class="text-gray-400">{service.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>