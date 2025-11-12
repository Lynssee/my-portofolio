<script>
	const skills = [
		'Web & App Development',
		'Network & Server Management',
		'Business Analysis',
		'System Design',
		'IT Infrastructure & Security',
		'Automation & Integration'
	];
	
	const experiences = [
		{
			title: 'Full Stack Developer',
			company: 'Eltamaprimaindo',
			period: 'May 2024 - Present',
			current: true,
			tasks: [
				'Mengembangkan aplikasi web & mobile dengan framework modern',
				'Mengintegrasikan AI untuk solusi digital yang efisien',
				'Mengelola infrastruktur server & jaringan untuk performa tinggi',
				'Menganalisa bisnis untuk merancang sistem yang optimal',
				'Mengimplementasikan solusi IT yang aman dan efisien',
				'Mengoptimasi proses bisnis untuk meningkatkan produktivitas',
				'Mengelola database untuk kebutuhan bisnis',
			]
		},
		{
			title: 'Technical Support',
			company: 'Citra Net',
			period: 'October 2023 - December 2023',
			current: false,
			tasks: [
				'Membantu pelanggan dalam mengatasi masalah teknis',
				'Menginstalasi & mengkonfigurasi perangkat lunak',
				'Mengoptimasi performa jaringan & server',
				'Mengatasi masalah hardware & software'
			]
		}
	];
</script>

<section id="about" class="py-20 px-6">
	<div class="max-w-7xl mx-auto">
		<h2 class="text-4xl font-bold text-center mb-12">About Me</h2>
		<div class="grid lg:grid-cols-2 gap-12 items-center">
			<div>
				<h3 class="text-2xl font-bold mb-4 text-neon">IT Professional & System Analyst</h3>
				<p class="text-gray-400 mb-6 leading-relaxed">
					Saya adalah seorang IT Professional dengan keahlian dalam pengembangan aplikasi, manajemen infrastruktur, 
					dan analisis sistem. Dengan latar belakang pendidikan Teknik Komputer dan Jaringan dari SMK Panca Bhakti Banjarnegara, 
					saya memiliki fondasi yang kuat dalam teknologi informasi dan pengembangan sistem.
				</p>
				<p class="text-gray-400 mb-8 leading-relaxed">
					Berpengalaman dalam merancang dan mengimplementasikan solusi IT yang aman dan efisien, 
					termasuk pengembangan sistem ERP untuk manufaktur yang terintegrasi. 
					Fokus saya meliputi pengembangan aplikasi web & mobile, manajemen server & jaringan, 
					analisis bisnis, serta otomasi proses untuk meningkatkan produktivitas organisasi.
				</p>
				
				<div class="grid grid-cols-2 gap-4">
					{#each skills as skill}
						<div class="flex items-center space-x-3">
							<svg class="w-4 h-4 text-neon flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
								<path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd"></path>
							</svg>
							<span>{skill}</span>
						</div>
					{/each}
				</div>
			</div>
			
			<div class="space-y-6">
				{#each experiences as exp}
					<div class="border-l-2 border-neon pl-6 relative">
						<div class="absolute -left-2 top-0 w-4 h-4 rounded-full {exp.current ? 'bg-neon' : 'bg-gray-700'}"></div>
						<h4 class="text-xl font-bold">{exp.title}</h4>
						<p class="text-neon">{exp.company}</p>
						<p class="text-gray-500 text-sm mb-2">{exp.period}</p>
						<ul class="text-gray-400 space-y-1 text-sm">
							{#each exp.tasks as task}
								<li class="flex items-start">
									<svg class="w-4 h-4 mr-2 mt-0.5 flex-shrink-0 {exp.current ? 'text-neon' : 'text-gray-500'}" fill="currentColor" viewBox="0 0 20 20">
										<path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"></path>
									</svg>
									<span>{task}</span>
								</li>
							{/each}
						</ul>
					</div>
				{/each}
			</div>
		</div>
	</div>
</section>