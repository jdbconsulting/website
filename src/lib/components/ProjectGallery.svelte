<script lang="ts">
	const projects = [
		{
			src: '/images/projects/project-1.jpg',
			alt: 'FPGA array for wireless digital signal processing (DSP) development',
			caption: 'FPGA Array'
		},
		{
			src: '/images/projects/project-2.jpg',
			alt: 'High-performance Software Defined Radio (SDR) development board',
			caption: 'SDR'
		},
		{
			src: '/images/projects/project-3.jpg',
			alt: 'High-efficiency resonant power converter for space applications',
			caption: 'Resonant Power Converter'
		},
		{
			src: '/images/projects/project-4.jpg',
			alt: 'Control unit for a tintable glass window',
			caption: 'Tintable Glass Window Controller'
		},
		{
			src: '/images/projects/project-5.jpg',
			alt: 'Lighting control unit for precion lab equipment',
			caption: 'Precision Lab Lighting Controller'
		},
		{
			src: '/images/projects/project-6.jpg',
			alt: 'FPGA controller for LiDAR system',
			caption: 'LiDAR Controller'
		}
	];

	let currentIndex = $state(0);
	let paused = $state(false);
	let intervalId: ReturnType<typeof setInterval> | null = null;

	function startAutoplay() {
		stopAutoplay();
		intervalId = setInterval(() => {
			if (!paused) currentIndex = (currentIndex + 1) % projects.length;
		}, 4000);
	}

	function stopAutoplay() {
		if (intervalId) clearInterval(intervalId);
	}

	function goTo(index: number) {
		currentIndex = index;
		startAutoplay();
	}

	function prev() {
		currentIndex = (currentIndex - 1 + projects.length) % projects.length;
		startAutoplay();
	}

	function next() {
		currentIndex = (currentIndex + 1) % projects.length;
		startAutoplay();
	}

	$effect(() => {
		startAutoplay();
		return stopAutoplay;
	});
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<section
	class="bg-navy-950 py-20 sm:py-28"
	onmouseenter={() => (paused = true)}
	onmouseleave={() => (paused = false)}
>
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center">
			<h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl">
				Previous Work
			</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-400">
				A selection of hardware projects from across our career.
			</p>
		</div>

		<div class="relative mx-auto mt-12 max-w-4xl">
			<div class="relative aspect-video overflow-hidden rounded-2xl border border-white/10 bg-navy-900">
				{#each projects as project, i}
					<div
						class="absolute inset-0 transition-opacity duration-700 ease-in-out"
						class:opacity-100={i === currentIndex}
						class:opacity-0={i !== currentIndex}
					>
						<img
							src={project.src}
							alt={project.alt}
							class="h-full w-full object-cover"
							loading={i === 0 ? 'eager' : 'lazy'}
						/>
						<div class="absolute inset-x-0 bottom-0 bg-linear-to-t from-black/70 to-transparent px-6 pb-6 pt-16">
							<p class="text-sm font-medium text-white/90">{project.caption}</p>
						</div>
					</div>
				{/each}

				<button
					onclick={prev}
					class="absolute left-3 top-1/2 -translate-y-1/2 rounded-full bg-black/40 p-2 text-white/80 backdrop-blur-sm transition-colors hover:bg-black/60 hover:text-white"
					aria-label="Previous project"
				>
					<svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
						<path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
					</svg>
				</button>
				<button
					onclick={next}
					class="absolute right-3 top-1/2 -translate-y-1/2 rounded-full bg-black/40 p-2 text-white/80 backdrop-blur-sm transition-colors hover:bg-black/60 hover:text-white"
					aria-label="Next project"
				>
					<svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
						<path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
					</svg>
				</button>
			</div>

			<div class="mt-6 flex justify-center gap-2">
				{#each projects as _, i}
					<button
						onclick={() => goTo(i)}
						class="h-2 rounded-full transition-all duration-300 {i === currentIndex
							? 'w-8 bg-accent-500'
							: 'w-2 bg-white/30 hover:bg-white/50'}"
						aria-label="Go to project {i + 1}"
					></button>
				{/each}
			</div>
		</div>
	</div>
</section>
