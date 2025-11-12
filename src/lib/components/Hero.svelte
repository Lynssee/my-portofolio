<script>
	import profilePhoto from '$lib/assets/profile-photo.jpg';

	const stats = [
		{ number: '1', suffix: '+', label: 'Years Experience' },
		{ number: '3', suffix: '+', label: 'Projects' },
		{ number: '6', suffix: '+', label: 'Skills' },
		{ number: '100', suffix: '%', label: 'Dedication' }
	];
</script>

<section id="home" class="min-h-screen flex items-center relative px-6 pt-20">
	<div class="absolute top-1/4 right-1/4 w-96 h-96 bg-neon/10 rounded-full blur-3xl animate-pulse"></div>
	
	<div class="max-w-7xl mx-auto grid lg:grid-cols-2 gap-12 items-center w-full">
		<!-- Foto di kiri (desktop & mobile) -->
		<div class="order-1 lg:order-1">
			<div class="relative w-80 h-96 mx-auto lg:mx-0">
				<div class="absolute inset-0 bg-gradient-to-br from-neon/20 to-transparent rounded-2xl blur-2xl"></div>
				<div class="relative w-full h-full rounded-2xl overflow-hidden border-2 border-neon/30 shadow-neon">
					<!-- Foto Profile dari pegunungan -->
					<img 
						src={profilePhoto} 
						alt="Sulthan Hafizh Pratama"
						class="w-full h-full object-cover object-center"
					/>
					<!-- Overlay gradient untuk efek -->
					<div class="absolute inset-0 bg-gradient-to-t from-dark/50 via-transparent to-transparent"></div>
				</div>
			</div>
		</div>
		
		<!-- Teks di kanan (desktop & mobile) -->
		<div class="order-2 lg:order-2">
			<p class="text-gray-400 uppercase tracking-widest mb-4">Hello I'm Afis</p>
			<h1 class="text-5xl lg:text-7xl font-bold mb-6">
				Fullstack <span class="text-neon">Developer</span>
			</h1>
			<p class="text-gray-400 text-lg mb-8 leading-relaxed">
				Full Stack Developer dengan pengalaman dalam membangun sistem enterprise seperti ERP manufaktur, sistem procurement, dan project management. Berfokus pada pengembangan solusi digital yang terintegrasi dengan AI untuk meningkatkan efisiensi bisnis.
			</p>
			
			<a href="#about" class="inline-block bg-neon text-dark px-8 py-3 rounded-full font-semibold uppercase tracking-wide hover:scale-105 transition-transform hover:shadow-lg hover:shadow-neon/30">
				About Me
			</a>
			
			<div class="grid grid-cols-2 md:grid-cols-4 gap-8 mt-12">
				{#each stats as stat}
					<div>
						<div class="text-3xl font-bold">
							{stat.number}<span class="text-neon">{stat.suffix}</span>
						</div>
						<div class="text-gray-500 text-sm">{stat.label}</div>
					</div>
				{/each}
			</div>
		</div>
	</div>
</section>

