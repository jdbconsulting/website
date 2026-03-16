<script lang="ts">
	interface Props {
		heading?: string;
		subheading?: string;
		detailed?: boolean;
	}

	let {
		heading = 'What We Do',
		subheading = 'End-to-end engineering consulting from strategy through proof-of-concept delivery.',
		detailed = false
	}: Props = $props();

	const services = [
		{
			title: 'System Engineering',
			description:
				'Block-diagram-level requirements capture and systems decomposition, aligned to your business goals and program milestones.',
			icon: 'system'
		},
		{
			title: 'PCB Design',
			description:
				'RF and electrical engineering from schematic capture through simulation — power integrity, signal integrity, and circuit-level analysis.',
			icon: 'pcb-design'
		},
		{
			title: 'PCB Layout',
			description:
				'World-class component placement and routing, with hands-on experience manufacturing virtually every type of PCB — rigid, flex, HDI, and RF.',
			icon: 'pcb-layout'
		},
		{
			title: 'Hardware Bringup',
			description:
				'Systematic debugging and validation of the most complex hardware systems, from first power-on through full functional verification.',
			icon: 'bringup'
		},
		{
			title: 'Embedded Software',
			description:
				'Digital design and firmware development for embedded systems — bare-metal, RTOS, and hardware-software co-design.',
			icon: 'code'
		},
		{
			title: 'Documentation & Team Leadership',
			description:
				'Thorough documentation of hardware milestones, design decisions, and test results — paired with hands-on technical team mentorship.',
			icon: 'docs'
		}
	];
</script>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">{heading}</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-600">{subheading}</p>
		</div>
		<div class="mt-16 grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
			{#each services as service}
				<div
					class="group rounded-2xl border border-slate-200 bg-white p-8 transition-all hover:border-slate-300 hover:shadow-lg"
				>
					<div
						class="flex h-12 w-12 items-center justify-center rounded-xl bg-navy-50 text-navy-600"
					>
						<svg
							class="h-6 w-6"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
							stroke-width="1.5"
							aria-hidden="true"
						>
						{#if service.icon === 'system'}
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M2.25 7.125C2.25 6.504 2.754 6 3.375 6h6c.621 0 1.125.504 1.125 1.125v3.75c0 .621-.504 1.125-1.125 1.125h-6a1.125 1.125 0 01-1.125-1.125v-3.75zM14.25 8.625c0-.621.504-1.125 1.125-1.125h5.25c.621 0 1.125.504 1.125 1.125v8.25c0 .621-.504 1.125-1.125 1.125h-5.25a1.125 1.125 0 01-1.125-1.125v-8.25zM3.75 16.125c0-.621.504-1.125 1.125-1.125h5.25c.621 0 1.125.504 1.125 1.125v2.25c0 .621-.504 1.125-1.125 1.125h-5.25a1.125 1.125 0 01-1.125-1.125v-2.25z"
							/>
						{:else if service.icon === 'pcb-design'}
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M8.25 3v1.5M4.5 8.25H3m18 0h-1.5M4.5 12H3m18 0h-1.5m-15 3.75H3m18 0h-1.5M8.25 19.5V21M12 3v1.5m0 15V21m3.75-18v1.5m0 15V21m-9-1.5h10.5a2.25 2.25 0 002.25-2.25V6.75a2.25 2.25 0 00-2.25-2.25H6.75A2.25 2.25 0 004.5 6.75v10.5a2.25 2.25 0 002.25 2.25zm.75-12h9v9h-9v-9z"
							/>
						{:else if service.icon === 'pcb-layout'}
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M6.429 9.75L2.25 12l4.179 2.25m0-4.5l5.571 3 5.571-3m-11.142 0L2.25 7.5 12 2.25l9.75 5.25-4.179 2.25m0 0L21.75 12l-4.179 2.25m0 0L12 16.5l-5.571-2.25m11.142 0L21.75 16.5 12 21.75 2.25 16.5l4.179-2.25"
							/>
						{:else if service.icon === 'bringup'}
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M21.75 6.75a4.5 4.5 0 01-4.884 4.484c-1.076-.091-2.264.071-2.95.904l-7.152 8.684a2.548 2.548 0 11-3.586-3.586l8.684-7.152c.833-.686.995-1.874.904-2.95a4.5 4.5 0 016.336-4.486l-3.276 3.276a2.25 2.25 0 002.25 2.25l3.276-3.276c.256.565.398 1.192.398 1.852z"
							/>
						{:else if service.icon === 'code'}
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5"
							/>
						{:else if service.icon === 'docs'}
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m0 12.75h7.5m-7.5 3H12M10.5 2.25H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z"
							/>
						{/if}
						</svg>
					</div>
					<h3 class="mt-6 text-lg font-semibold text-slate-900">{service.title}</h3>
					<p class="mt-2 text-sm leading-relaxed text-slate-600">{service.description}</p>
					{#if detailed}
						<a
							href="/contact"
							class="mt-4 inline-flex items-center gap-1 text-sm font-medium text-navy-700 transition-colors hover:text-accent-600"
						>
							Learn more
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
					{/if}
				</div>
			{/each}
		</div>
	</div>
</section>
