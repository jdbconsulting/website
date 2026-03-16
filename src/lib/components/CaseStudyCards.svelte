<script lang="ts">
	const studies = [
		{
			category: 'High Performance Computing',
			title: 'FPGA Based ONNX Runtime Hardware',
			description:
				'Designed a custom FPGA execution provider for ONNX Runtime, delivering sub-millisecond inference at under 5 W for hard real-time edge ML applications.',
			result: 'HPC',
			href: '/case-studies/fpga-onnx-runtime'
		},
		{
			category: 'Embedded Systems & IoT',
			title: 'Low-Powered Lidar With Cellular Backhaul',
			description:
				'Built a solar/battery-powered remote sensing platform around an STM32F7 MCU with 3G cellular uplink, engineered for 3+ years of unattended operation.',
			result: 'IoT',
			href: '/case-studies/low-power-lidar-cellular'
		}
	];
</script>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="grid gap-8 sm:grid-cols-2">
			{#each studies as study}
				<article
					class="group flex flex-col overflow-hidden rounded-2xl border border-slate-200 transition-all hover:border-slate-300 hover:shadow-lg"
				>
					<div class="flex h-48 items-center justify-center bg-gradient-to-br from-navy-50 to-slate-100">
						<div
							class="flex h-16 w-16 items-center justify-center rounded-2xl bg-white shadow-sm"
						>
							<svg
								class="h-8 w-8 text-navy-400"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
								stroke-width="1"
								aria-hidden="true"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									d="M2.25 12.75V12A2.25 2.25 0 014.5 9.75h15A2.25 2.25 0 0121.75 12v.75m-8.69-6.44l-2.12-2.12a1.5 1.5 0 00-1.061-.44H4.5A2.25 2.25 0 002.25 6v12a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18V9a2.25 2.25 0 00-2.25-2.25h-5.379a1.5 1.5 0 01-1.06-.44z"
								/>
							</svg>
						</div>
					</div>
					<div class="flex flex-1 flex-col p-6">
						<div class="flex items-center gap-3">
							<span
								class="rounded-full bg-navy-50 px-3 py-1 text-xs font-medium text-navy-700"
								>{study.category}</span
							>
							<span class="text-xs font-medium text-accent-600">{study.result}</span>
						</div>
						<h3 class="mt-3 text-lg font-semibold text-slate-900">{study.title}</h3>
						<p class="mt-2 flex-1 text-sm leading-relaxed text-slate-600">
							{study.description}
						</p>
					<a
						href={study.href || '/contact'}
						class="mt-4 inline-flex items-center gap-1 text-sm font-medium text-navy-700 transition-colors hover:text-accent-600"
					>
						{study.href ? 'Read full study' : 'Discuss this project'}
							<svg
								class="h-4 w-4 transition-transform group-hover:translate-x-0.5"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
								stroke-width="2"
								aria-hidden="true"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"
								/>
							</svg>
						</a>
					</div>
				</article>
			{/each}
		</div>
	</div>
</section>
