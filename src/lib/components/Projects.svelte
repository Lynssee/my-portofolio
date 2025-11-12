<script>
	// Import gambar projects yang tersedia
	import ERP from '$lib/assets/projects/ERP.png';
	import DailyProject from '$lib/assets/projects/DailyProject.png';

	// Import slideshow images untuk ERP
	import erpImg1 from '$lib/assets/projects/erp/finance-invoice.png';
	import erpImg2 from '$lib/assets/projects/erp/inv-dashboard.png';
	import erpImg3 from '$lib/assets/projects/erp/inv-delivery-order.png';
	import erpImg4 from '$lib/assets/projects/erp/inv-history.png';
	import erpImg5 from '$lib/assets/projects/erp/inv-stock-management.png';
	import erpImg6 from '$lib/assets/projects/erp/production-formulamanagement.png';
	import erpImg7 from '$lib/assets/projects/erp/production-workorder.png';
	import erpImg8 from '$lib/assets/projects/erp/rmc-formula.png';
	import erpImg9 from '$lib/assets/projects/erp/sales_customer.png';
	import erpImg10 from '$lib/assets/projects/erp/sales-dashboard.png';
	import erpImg11 from '$lib/assets/projects/erp/sales-po-customer.png';

	// Import slideshow images untuk Project Management
	import projectImg1 from '$lib/assets/projects/project/detail projcet.png';
	import projectImg2 from '$lib/assets/projects/project/dokumentasi.png';
	import projectImg3 from '$lib/assets/projects/project/laporan.png';

	// Modal state
	let showModal = $state(false);
	let selectedProject = $state(null);
	let currentSlideIndex = $state(0);

	const projects = [
		{
			title: "ERP Manufacturing System",
			description:
				"Comprehensive ERP solution for manufacturing industry with production planning, inventory management, and real-time reporting",
			category: "Web Development",
			image: ERP,
			slideImages: [erpImg1, erpImg2, erpImg3, erpImg4, erpImg5, erpImg6, erpImg7, erpImg8, erpImg9, erpImg10, erpImg11],
			technologies: [
				"Svelte",
				"Tailwindcss",
				"Directus",
				"Node.js",
				"Docker",
				"Cloudflare",
			],
			link: "ERP",
			github: "#",
		},
		{
			title: "Project Management System",
			description:
				"Project management system for project management department with automated alerts and performance analytics",
			category: "Web Development",
			image: DailyProject,
			slideImages: [projectImg1, projectImg2, projectImg3],
			technologies: [
				"Svelte",
				"Tailwindcss",
				"Directus",
				"Node.js",
				"Docker",
				"Cloudflare",
			],
			link: "project",
			github: "#",
		},
		{
			title: "Procurement Management System",
			description:
				"Procurement management system for procurement department with automated alerts and performance analytics",
			category: "Web Development",
			image: null,
			slideImages: [],
			technologies: [
				"Svelte",
				"Tailwindcss",
				"Directus",
				"Node.js",
				"Docker",
				"Cloudflare",
			],
			link: "procurement",
			github: "#",
		},
		{
			title: "WhatsApp Notification System",
			description:
				"Automated WhatsApp notification system with real-time alerts and message scheduling for business communications",
			category: "Automation",
			image: null,
			slideImages: [],
			technologies: ["Node.js", "WhatsApp API"],
			link: "Whatsapp",
			github: "#",
		},
		{
			title: "Directus Headless CMS",
			description:
				"Centralized backend system with Directus for data management, multi-level approval workflows, and API integration",
			category: "Backend Development",
			image: null,
			slideImages: [],
			technologies: ["Directus", "PostgreSQL", "Docker"],
			link: "directus",
			github: "#",
		},
		{
			title: "Server & Infrastructure Management",
			description:
				"Deployed and maintained Linux-based servers for ERP, CCTV, and internal systems using Docker and Cloudflare Tunnel",
			category: "Infrastructure",
			image: null,
			slideImages: [],
			technologies: ["Linux", "Docker", "Cloudflare Tunnel", "VPS"],
			link: "server-management",
			github: "#",
		},
		{
			title: "Network Topology Design",
			description:
				"Designed and implemented hybrid network topology through extensive testing and optimization, managing network infrastructure for optimal performance",
			category: "Infrastructure",
			image: null,
			slideImages: [],
			technologies: ["Network Design", "Topology Planning", "VLAN", "Router Configuration"],
			link: "network-design",
			github: "#",
		},
		{
			title: "CCTV System Integration",
			description:
				"Implemented and maintained analog CCTV systems with DVR recording, remote monitoring, and secure access configuration",
			category: "Infrastructure",
			image: null,
			slideImages: [],
			technologies: ["Analog CCTV", "DVR", "Remote Access", "Video Surveillance"],
			link: "cctv-system",
			github: "#",
		},
		{
			title: "VPS Deployment & CI/CD",
			description:
				"Managed VPS environments for production systems with automated CI/CD pipelines and containerized deployment",
			category: "DevOps",
			image: null,
			slideImages: [],
			technologies: ["VPS", "GitHub Actions", "Docker", "Cloudflare"],
			link: "vps-deployment",
			github: "#",
		},
	];

	let selectedCategory = $state("all");
	const categories = [
		"all",
		"Web Development",
		"Backend Development",
		"Infrastructure",
		"DevOps",
		"Automation"
	];

	const filteredProjects = $derived(
		selectedCategory === "all"
			? projects
			: projects.filter((p) => p.category === selectedCategory),
	);

	// Function to handle image error
	function handleImageError(event) {
		const img = event.target;
		img.style.display = "none";
		const fallback = img.nextElementSibling;
		if (fallback) {
			fallback.style.display = "flex";
		}
	}

	// Modal functions
	function openModal(project) {
		selectedProject = project;
		currentSlideIndex = 0;
		showModal = true;
		document.body.style.overflow = 'hidden';
	}

	function closeModal() {
		showModal = false;
		selectedProject = null;
		document.body.style.overflow = 'auto';
	}

	function nextSlide() {
		if (selectedProject && selectedProject.slideImages.length > 0) {
			currentSlideIndex = (currentSlideIndex + 1) % selectedProject.slideImages.length;
		}
	}

	function prevSlide() {
		if (selectedProject && selectedProject.slideImages.length > 0) {
			currentSlideIndex = currentSlideIndex === 0 
				? selectedProject.slideImages.length - 1 
				: currentSlideIndex - 1;
		}
	}

	function goToSlide(index) {
		currentSlideIndex = index;
	}
</script>

<section id="projects" class="py-20 px-6 bg-dark-secondary">
	<div class="max-w-7xl mx-auto">
		<h2 class="text-4xl font-bold text-center mb-4">Featured Projects</h2>
		<p class="text-gray-400 text-center mb-12">Some of my recent work</p>

		<!-- Category Filter -->
		<div class="flex flex-wrap justify-center gap-4 mb-12">
			{#each categories as category}
				<button
					onclick={() => (selectedCategory = category)}
					class="px-6 py-2 rounded-full transition-all {selectedCategory ===
					category
						? 'bg-neon text-dark'
						: 'bg-dark border border-gray-700 hover:border-neon/50'}"
				>
					{category}
				</button>
			{/each}
		</div>

		<!-- Projects Grid -->
		<div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
			{#each filteredProjects as project}
				<div
					class="group relative overflow-hidden rounded-2xl border border-gray-800 hover:border-neon/50 transition-all bg-dark cursor-pointer"
					onclick={() => openModal(project)}
					role="button"
					tabindex="0"
				>
					<!-- Project Image atau Youtube/Social Media Video -->
					<div class="aspect-video overflow-hidden relative bg-black">
						{#if project.youtube}
							<!-- YouTube iframe -->
							<iframe
								src={project.youtube}
								title={project.title + " - YouTube Video"}
								loading="lazy"
								class="w-full h-full border-0"
								allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
								allowfullscreen
								style="border: none;"
							></iframe>
						{:else if project.instagram}
							<!-- Instagram Reel embed -->
							<iframe
								src={project.instagram}
								title={project.title + " - Instagram Reel"}
								loading="lazy"
								class="w-full h-full border-0"
								scrolling="no"
								allowtransparency="true"
								allowfullscreen
								style="border: none; background: white;"
							></iframe>
						{:else if project.tiktok}
							<!-- TikTok embed -->
							<iframe
								src={project.tiktok}
								title={project.title + " - TikTok Video"}
								loading="lazy"
								class="w-full h-full border-0"
								allowfullscreen
								scrolling="no"
								allow="encrypted-media;"
								style="border: none; background: black;"
							></iframe>
						{:else if project.image}
							<img
								src={project.image}
								alt={project.title}
								loading="lazy"
								class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
								onerror={handleImageError}
							/>
							<!-- Fallback jika gambar gagal load -->
							<div
								class="w-full h-full bg-gradient-to-br from-neon/20 to-purple-600/20 items-center justify-center hidden"
							>
								<span class="text-4xl text-neon/50">🖼️</span>
							</div>
						{:else}
							<!-- Placeholder jika belum ada gambar -->
							<div
								class="w-full h-full bg-gradient-to-br from-neon/20 to-purple-600/20 flex items-center justify-center"
							>
								<div class="text-center">
									<span
										class="text-4xl text-neon/50 mb-2 block"
										>📁</span
									>
									<p class="text-gray-400 text-sm">
										Coming Soon
									</p>
								</div>
							</div>
						{/if}
					</div>

					<!-- Project Info -->
					<div class="p-6">
						<span class="text-neon text-sm font-medium"
							>{project.category}</span
						>
						<h3 class="text-xl font-bold mt-2 mb-2 text-white">
							{project.title}
						</h3>
						<p class="text-gray-400 text-sm mb-4 leading-relaxed">
							{project.description}
						</p>

						<!-- Technologies -->
						<div class="flex flex-wrap gap-2 mb-4">
							{#each project.technologies as tech}
								<span
									class="text-xs px-3 py-1 bg-dark-secondary rounded-full text-gray-300 border border-gray-700"
								>
									{tech}
								</span>
							{/each}
						</div>

						<!-- Links -->
						<div class="flex gap-4">
							{#if project.link !== "#"}
								<a
									href={project.link}
									target="_blank"
									class="text-neon hover:text-white transition-colors"
									title="Live Demo"
								>
									<svg
										class="w-5 h-5"
										fill="none"
										stroke="currentColor"
										viewBox="0 0 24 24"
									>
										<path
											stroke-linecap="round"
											stroke-linejoin="round"
											stroke-width="2"
											d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
										></path>
									</svg>
								</a>
							{/if}

							{#if project.github !== "#"}
								<a
									href={project.github}
									target="_blank"
									class="text-neon hover:text-white transition-colors"
									title="Source Code"
								>
									<svg
										class="w-5 h-5"
										fill="currentColor"
										viewBox="0 0 24 24"
									>
										<path
											d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
										/>
									</svg>
								</a>
							{/if}

							{#if project.youtube}
								<a
									href="https://www.youtube.com/watch?v=zb-KDX6GRiM"
									target="_blank"
									class="text-red-500 hover:text-red-400 transition-colors"
									title="Watch on YouTube"
								>
									<svg
										class="w-5 h-5"
										fill="currentColor"
										viewBox="0 0 24 24"
									>
										<path
											d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"
										/>
									</svg>
								</a>
							{/if}

							{#if project.instagram}
								<a
									href="https://www.instagram.com/reel/DHBbS2IyZzp/"
									target="_blank"
									class="text-pink-500 hover:text-pink-400 transition-colors"
									title="View on Instagram"
								>
									<svg
										class="w-5 h-5"
										fill="currentColor"
										viewBox="0 0 24 24"
									>
										<path
											d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zM5.838 12a6.162 6.162 0 1 1 12.324 0 6.162 6.162 0 0 1-12.324 0zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm4.965-10.405a1.44 1.44 0 1 1 2.881.001 1.44 1.44 0 0 1-2.881-.001z"
										/>
									</svg>
								</a>
							{/if}

							{#if project.tiktok}
								<a
									href="https://vt.tiktok.com/ZSAUMvswu/"
									target="_blank"
									class="text-white hover:text-gray-300 transition-colors"
									title="View on TikTok"
								>
									<svg
										class="w-5 h-5"
										fill="currentColor"
										viewBox="0 0 24 24"
									>
										<path
											d="M12.525.02c1.31-.02 2.61-.01 3.91-.02.08 1.53.63 3.09 1.75 4.17 1.12 1.11 2.7 1.62 4.24 1.79v4.03c-1.44-.05-2.89-.35-4.2-.97-.57-.26-1.1-.59-1.62-.93-.01 2.92.01 5.84-.02 8.75-.08 1.4-.54 2.79-1.35 3.94-1.31 1.92-3.58 3.17-5.91 3.21-1.43.08-2.86-.31-4.08-1.03-2.02-1.19-3.44-3.37-3.65-5.71-.02-.5-.03-1-.01-1.49.18-1.9 1.12-3.72 2.58-4.96 1.66-1.44 3.98-2.13 6.15-1.72.02 1.48-.04 2.96-.04 4.44-.99-.32-2.15-.23-3.02.37-.63.41-1.11 1.04-1.36 1.75-.21.51-.15 1.07-.14 1.61.24 1.64 1.82 3.02 3.5 2.87 1.12-.01 2.19-.66 2.77-1.61.19-.33.4-.67.41-1.06.1-1.79.06-3.57.07-5.36.01-4.03-.01-8.05.02-12.07z"
										/>
									</svg>
								</a>
							{/if}
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Modal Popup with Slideshow -->
{#if showModal && selectedProject}
	<div 
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/90 p-4"
		onclick={closeModal}
		role="dialog"
		aria-modal="true"
	>
		<div 
			class="relative max-w-5xl w-full bg-dark rounded-2xl overflow-hidden border border-gray-800"
			onclick={(e) => e.stopPropagation()}
		>
			<!-- Close Button -->
			<button
				onclick={closeModal}
				class="absolute top-4 right-4 z-10 w-10 h-10 bg-dark/80 hover:bg-neon rounded-full flex items-center justify-center transition-colors group"
				aria-label="Close modal"
			>
				<svg class="w-6 h-6 text-white group-hover:text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
				</svg>
			</button>

			<!-- Slideshow Area -->
			<div class="relative aspect-video bg-black">
				{#if selectedProject.slideImages && selectedProject.slideImages.length > 0}
					<!-- Slideshow Images -->
					<img 
						src={selectedProject.slideImages[currentSlideIndex]} 
						alt={`${selectedProject.title} - Image ${currentSlideIndex + 1}`}
						class="w-full h-full object-contain"
					/>

					<!-- Navigation Arrows -->
					{#if selectedProject.slideImages.length > 1}
						<button
							onclick={prevSlide}
							class="absolute left-4 top-1/2 -translate-y-1/2 w-12 h-12 bg-dark/80 hover:bg-neon rounded-full flex items-center justify-center transition-colors group"
							aria-label="Previous slide"
						>
							<svg class="w-6 h-6 text-white group-hover:text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
							</svg>
						</button>

						<button
							onclick={nextSlide}
							class="absolute right-4 top-1/2 -translate-y-1/2 w-12 h-12 bg-dark/80 hover:bg-neon rounded-full flex items-center justify-center transition-colors group"
							aria-label="Next slide"
						>
							<svg class="w-6 h-6 text-white group-hover:text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
							</svg>
						</button>

						<!-- Slide Indicators -->
						<div class="absolute bottom-4 left-1/2 -translate-x-1/2 flex gap-2">
							{#each selectedProject.slideImages as _, index}
								<button
									onclick={() => goToSlide(index)}
									class="w-2 h-2 rounded-full transition-all {currentSlideIndex === index ? 'bg-neon w-8' : 'bg-gray-500 hover:bg-gray-400'}"
									aria-label={`Go to slide ${index + 1}`}
								></button>
							{/each}
						</div>
					{/if}
				{:else}
					<!-- No slideshow images, show main image -->
					<img 
						src={selectedProject.image} 
						alt={selectedProject.title}
						class="w-full h-full object-contain"
					/>
				{/if}
			</div>

			<!-- Project Details -->
			<div class="p-6">
				<span class="text-neon text-sm font-medium">{selectedProject.category}</span>
				<h3 class="text-2xl font-bold mt-2 mb-3 text-white">{selectedProject.title}</h3>
				<p class="text-gray-400 mb-4 leading-relaxed">{selectedProject.description}</p>

				<!-- Technologies -->
				<div class="flex flex-wrap gap-2 mb-4">
					{#each selectedProject.technologies as tech}
						<span class="text-xs px-3 py-1 bg-dark-secondary rounded-full text-gray-300 border border-gray-700">
							{tech}
						</span>
					{/each}
				</div>

				<!-- Links -->
				<div class="flex gap-4">
					{#if selectedProject.link !== "#"}
						<a
							href={selectedProject.link}
							target="_blank"
							class="inline-flex items-center gap-2 px-6 py-2 bg-neon text-dark rounded-full font-semibold hover:scale-105 transition-transform"
							onclick={(e) => e.stopPropagation()}
						>
							<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
							</svg>
							View Live
						</a>
					{/if}

					{#if selectedProject.github !== "#"}
						<a
							href={selectedProject.github}
							target="_blank"
							class="inline-flex items-center gap-2 px-6 py-2 border border-neon text-neon rounded-full font-semibold hover:bg-neon hover:text-dark transition-all"
							onclick={(e) => e.stopPropagation()}
						>
							<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
								<path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z" />
							</svg>
							Source Code
						</a>
					{/if}
				</div>
			</div>
		</div>
	</div>
{/if}
