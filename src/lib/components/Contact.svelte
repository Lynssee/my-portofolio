<script>
	// Import CV from assets folder
	// import cvFile from '$lib/assets/C.V SulthanHafizh.pdf';
	
	const contacts = [
		{
			href: 'mailto:sulthanhafizh137@gmail.com',
			label: 'sulthanhafizh137@gmail.com',
			icon: 'M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z'
		},
		{
			href: 'tel:+6287766622494',
			label: '+62 877-6662-2494',
			icon: 'M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z'
		},
		{
			href: 'https://instagram.com/sulthanhafis',
			label: '@sulthanhafis',
			icon: 'M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zM5.838 12a6.162 6.162 0 1112.324 0 6.162 6.162 0 01-12.324 0zM12 16a4 4 0 110-8 4 4 0 010 8zm4.965-10.405a1.44 1.44 0 112.881.001 1.44 1.44 0 01-2.881-.001z'
		}
	];

	// Function to handle CV download
	function downloadCV() {
		const link = document.createElement('a');
		link.href = cvFile;
		link.download = 'CV_Sulthan_Hafizh_Pratama.pdf';
		link.click();
	}
</script>

<section id="contact" class="py-20 px-6">
	<div class="max-w-4xl mx-auto text-center">
		<h2 class="text-4xl font-bold mb-8">Let's Work Together</h2>
		<p class="text-gray-400 mb-12 text-lg">
			Feel free to reach out for collaborations or just a friendly hello
		</p>
		
		<div class="flex flex-wrap justify-center gap-6">
			{#each contacts as contact}
				<a 
					href={contact.href}
					target={contact.href.startsWith('http') ? '_blank' : undefined}
					rel={contact.href.startsWith('http') ? 'noopener noreferrer' : undefined}
					class="flex items-center space-x-3 bg-dark-secondary px-6 py-3 rounded-full hover:bg-neon hover:text-dark transition-colors group"
				>
					<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
						<path d={contact.icon}></path>
					</svg>
					<span>{contact.label}</span>
				</a>
			{/each}
		</div>
		
		<div class="mt-12">
			<button 
				onclick={downloadCV}
				class="inline-flex items-center gap-2 bg-neon text-dark px-8 py-3 rounded-full font-semibold uppercase tracking-wide hover:scale-105 transition-transform"
			>
				<svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
					<path fill-rule="evenodd" d="M3 17a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zm3.293-7.707a1 1 0 011.414 0L9 10.586V3a1 1 0 112 0v7.586l1.293-1.293a1 1 0 111.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z" clip-rule="evenodd"></path>
				</svg>
				Download CV
			</button>
		</div>
	</div>
</section>