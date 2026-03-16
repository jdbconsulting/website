<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Hero from '$lib/components/Hero.svelte';

	const tools = [
		{
			href: '/tools/pcb-via-thermal-solver',
			title: 'PCB Via Thermal Solver',
			description:
				'Calculate effective through-plane thermal conductivity for PCB via-stitching patterns. Determine temperature rise across your board for a given heat load.',
			category: 'Thermal Analysis'
		}
	];
</script>

<Seo
	title="Engineering Tools"
	description="Free online calculators and tools for electrical and computer engineers. Thermal analysis, PCB design, and more."
/>

<Hero
	title="Engineering Tools"
	subtitle="Free online calculators and analysis tools for electrical and computer engineers."
	compact
/>

<section class="bg-white py-16 sm:py-20">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
			{#each tools as tool}
				<a
					href={tool.href}
					class="group rounded-2xl border border-slate-200 bg-white p-6 transition-all hover:border-accent-300 hover:shadow-md"
				>
					<span class="text-xs font-semibold uppercase tracking-wider text-accent-500"
						>{tool.category}</span
					>
					<h3 class="mt-2 text-lg font-semibold text-slate-900 group-hover:text-navy-700">
						{tool.title}
					</h3>
					<p class="mt-2 text-sm leading-relaxed text-slate-600">{tool.description}</p>
					<span
						class="mt-4 inline-flex items-center gap-1 text-sm font-medium text-accent-600 group-hover:text-accent-500"
					>
						Open tool
						<svg
							class="h-4 w-4 transition-transform group-hover:translate-x-0.5"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
							stroke-width="2"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"
							/>
						</svg>
					</span>
				</a>
			{/each}
		</div>
	</div>
</section>
