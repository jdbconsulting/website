<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Cta from '$lib/components/Cta.svelte';

	const DOT_R = 7;
	const LOGO_BG = 32;
	const LOGO_IMG = 28;
	const LOGO_PAD = 2;

	interface TimelineEntry {
		date: string;
		title: string;
		description: string;
		highlight?: boolean;
		badge?: string;
		logos?: string[];
	}

	const entries: TimelineEntry[] = [
		{
			date: 'September 2009',
			title: 'Brinton Research LLC',
			description: 'Founded to develop CAD software for electromagnetic field solving.',
			logos: ['/images/logos/brinton-research.png']
		},
		{
			date: 'June 2010',
			title: 'Brinton Engineering LLC',
			description:
				'Brinton Research assets sold to newly formed Brinton Engineering LLC, providing computer and electrical engineering services in Menlo Park, California.',
			badge: 'Assets acquired',
			logos: ['/images/logos/brinton-engineering.png']
		},
		{
			date: 'November 2014',
			title: 'Signal Laboratories, Inc.',
			description:
				'Brinton Engineering assets sold to Signal Laboratories — a venture-backed startup. Venture-backed wireless broadband under Fordable brand name.',
			badge: 'Assets acquired',
			logos: ['/images/logos/siglabs.png', '/images/logos/fordable.png']
		},
		{
			date: 'November 2018',
			title: 'Amaya Tech, Inc. Founded',
			description:
				'Independently incorporated in California as an electrical engineering consulting firm.',
			logos: ['/images/logos/amaya-tech.png']
		},
		{
			date: '2020',
			title: 'Siglabs Assets Acquired',
			description:
				'Signal Laboratories wound down. Its assets were acquired by Amaya Tech, reuniting the engineering lineage under one roof.',
			highlight: true,
			badge: 'Merge'
		},
		{
			date: 'May 2021',
			title: 'DBA "Electron Labs"',
			description:
				'Amaya Tech began operating under the fictitious business name "Electron Labs."',
			logos: ['/images/logos/electron-labs.png']
		},
		{
			date: 'March 2026',
			title: 'Company Split',
			description:
				'Restructured into two separate entities: Electron Labs (sold) and JDBC — JD Brinton Consulting, Inc.',
			highlight: true,
			badge: 'Split'
		}
	];

	// Desktop graph constants
	const LEFT_X = 250;
	const RIGHT_X = 550;
	const CENTER_X = 400;
	const GFX_W = 800;
	const SPLIT_LEFT_X = CENTER_X - 130;
	const SPLIT_RIGHT_X = CENTER_X + 130;

	const Y = {
		brintonRes: 60,
		brintonEng: 180,
		sigLabs: 300,
		amayaTech: 380,
		merge: 490,
		electronLabs: 600,
		split: 710,
		splitEnd: 810
	};

	const GFX_H = Y.splitEnd + 80;

	const LABEL_WITH_LOGO = DOT_R + 6 + LOGO_BG + 8;

	interface LogoNode {
		x: number;
		y: number;
		src: string;
	}

	const desktopLogos: LogoNode[] = [
		{ x: LEFT_X + DOT_R + 6, y: Y.brintonRes - LOGO_BG / 2, src: '/images/logos/brinton-research.png' },
		{ x: LEFT_X + DOT_R + 6, y: Y.brintonEng - LOGO_BG / 2, src: '/images/logos/brinton-engineering.png' },
		{ x: LEFT_X + DOT_R + 6, y: Y.sigLabs - LOGO_BG / 2, src: '/images/logos/siglabs.png' },
		{ x: LEFT_X + DOT_R + 6 + LOGO_BG + 4, y: Y.sigLabs - LOGO_BG / 2, src: '/images/logos/fordable.png' },
		{ x: RIGHT_X + DOT_R + 6, y: Y.amayaTech - LOGO_BG / 2, src: '/images/logos/amaya-tech.png' },
		{ x: CENTER_X + DOT_R + 6, y: Y.electronLabs - LOGO_BG / 2, src: '/images/logos/electron-labs.png' },
		{ x: SPLIT_LEFT_X - LOGO_BG / 2, y: Y.splitEnd - DOT_R - 6 - LOGO_BG, src: '/images/logos/electron-labs.png' },
		{ x: SPLIT_RIGHT_X - LOGO_BG / 2, y: Y.splitEnd - DOT_R - 6 - LOGO_BG, src: '/images/logos/jdbc.png' }
	];
</script>

<Seo
	title="History"
	description="The history of JDBC — from Brinton Research in 2009 through Signal Labs, Amaya Tech, and Electron Labs to JD Brinton Consulting today."
/>

<section class="relative overflow-hidden bg-navy-950">
	<div
		class="absolute inset-0 bg-[radial-gradient(ellipse_at_top_right,rgba(59,130,246,0.12),transparent_60%)]"
		aria-hidden="true"
	></div>
	<div class="relative mx-auto max-w-7xl px-4 py-16 sm:px-6 sm:py-20 lg:px-8 lg:py-24">
		<a
			href="/about"
			class="inline-flex items-center gap-1.5 text-sm font-medium text-slate-400 transition-colors hover:text-white"
		>
			<svg
				class="h-4 w-4"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
				stroke-width="2"
				aria-hidden="true"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18"
				/>
			</svg>
			About JDBC
		</a>
		<h1 class="mt-6 max-w-4xl text-4xl font-bold tracking-tight text-white sm:text-5xl">
			Our History
		</h1>
		<p class="mt-4 max-w-2xl text-lg leading-relaxed text-slate-300">
			From electromagnetic field solvers to venture-backed wireless to the consulting practice you
			see today — the full lineage of JDBC.
		</p>
	</div>
</section>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-3xl">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
				How We Got Here
			</h2>
			<div class="mt-6 space-y-5 text-base leading-relaxed text-slate-600">
				<p>
					JDBC's story begins with <strong class="text-slate-800">Brinton Research LLC</strong>,
					founded in September 2009 to develop CAD software for electromagnetic field solving. In
					June 2010, Brinton Research's assets were sold to the newly formed
					<strong class="text-slate-800">Brinton Engineering LLC</strong>, which provided computer
					and electrical engineering services from Menlo Park, California.
				</p>
				<p>
					In November 2014, Brinton Engineering's assets were sold to
					<strong class="text-slate-800">Signal Laboratories, Inc.</strong> (Siglabs) — a
					venture-backed startup designing coherent wireless technology for last-mile broadband
					delivery.
				</p>
				<p>
					Meanwhile, <strong class="text-slate-800">Amaya Tech, Inc.</strong> was independently
					incorporated in November 2018 as a California corporation providing electrical engineering
					consulting. In 2020, when Signal Laboratories wound down, its assets were acquired by
					Amaya Tech — reuniting the engineering lineage under one roof.
				</p>
				<p>
					In May 2021, Amaya Tech began operating under the fictitious business name
					<strong class="text-slate-800">"Electron Labs"</strong>, expanding its focus into
					embedded systems, custom hardware development, and rapid prototyping.
				</p>
				<p>
					In March 2026, the company was restructured and split into two separate entities.
					<strong class="text-slate-800">Electron Labs</strong> was sold as its own company, and
					<strong class="text-slate-800">JDBC</strong> (JD Brinton Consulting, Inc.) was
					established as the successor consulting practice — carrying forward the same leadership,
					expertise, and commitment to ambitious engineering.
				</p>
			</div>
		</div>
	</div>
</section>

<section class="border-t border-slate-100 bg-slate-50 py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center lg:max-w-4xl">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
				Company Timeline
			</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-600">
				Two lineages converge, then split — from first incorporation to today.
			</p>
		</div>

		<!-- Desktop graph (two-track merge + split) -->
		<div class="mx-auto mt-16 hidden max-w-3xl lg:block">
			<svg
				viewBox="0 0 {GFX_W} {GFX_H}"
				fill="none"
				class="mx-auto w-full font-sans"
				role="img"
				aria-label="Company timeline showing Brinton Research, Brinton Engineering, and Signal Labs merging into Amaya Tech, then splitting into Electron Labs and JDBC"
			>
				<!-- Left track: Brinton Research → Brinton Engineering → Signal Labs → merge -->
				<line
					x1={LEFT_X}
					y1={Y.brintonRes}
					x2={LEFT_X}
					y2={Y.sigLabs + 55}
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
				/>
				<path
					d="M {LEFT_X} {Y.sigLabs + 55} C {LEFT_X} {Y.merge - 25}, {CENTER_X} {Y.merge - 25}, {CENTER_X} {Y.merge}"
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
					fill="none"
				/>

				<!-- Right track: Amaya Tech → merge -->
				<line
					x1={RIGHT_X}
					y1={Y.amayaTech}
					x2={RIGHT_X}
					y2={Y.amayaTech + 48}
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
				/>
				<path
					d="M {RIGHT_X} {Y.amayaTech + 48} C {RIGHT_X} {Y.merge - 15}, {CENTER_X} {Y.merge - 15}, {CENTER_X} {Y.merge}"
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
					fill="none"
				/>

				<!-- Center track: merge → Electron Labs → split -->
				<line
					x1={CENTER_X}
					y1={Y.merge}
					x2={CENTER_X}
					y2={Y.split}
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
				/>

				<!-- Split curves -->
				<path
					d="M {CENTER_X} {Y.split} C {CENTER_X} {Y.split + 50}, {SPLIT_LEFT_X} {Y.split + 50}, {SPLIT_LEFT_X} {Y.splitEnd}"
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
					fill="none"
				/>
				<path
					d="M {CENTER_X} {Y.split} C {CENTER_X} {Y.split + 50}, {SPLIT_RIGHT_X} {Y.split + 50}, {SPLIT_RIGHT_X} {Y.splitEnd}"
					stroke="#b3c2e0"
					stroke-width="2.5"
					stroke-linecap="round"
					fill="none"
				/>

				<!-- Transition annotations on left track -->
				<text
					x={LEFT_X + DOT_R + 6 + LOGO_BG + 6}
					y={(Y.brintonRes + Y.brintonEng) / 2 + 3}
					style="font-size: 10px; fill: #94a3b8; font-style: italic"
				>
					assets sold
				</text>
				<text
					x={LEFT_X + DOT_R + 6 + LOGO_BG + 6}
					y={(Y.brintonEng + Y.sigLabs) / 2 + 3}
					style="font-size: 10px; fill: #94a3b8; font-style: italic"
				>
					assets sold
				</text>
				<text
					x={LEFT_X + DOT_R + 6 + LOGO_BG + 6}
					y={Y.sigLabs + 40}
					style="font-size: 10px; fill: #94a3b8; font-style: italic"
				>
					wound down
				</text>

				<!-- Dots — left track -->
				<circle
					cx={LEFT_X}
					cy={Y.brintonRes}
					r={DOT_R}
					fill="#1a2744"
					stroke="white"
					stroke-width="3"
				/>
				<circle
					cx={LEFT_X}
					cy={Y.brintonEng}
					r={DOT_R}
					fill="#1a2744"
					stroke="white"
					stroke-width="3"
				/>
				<circle
					cx={LEFT_X}
					cy={Y.sigLabs}
					r={DOT_R}
					fill="#1a2744"
					stroke="white"
					stroke-width="3"
				/>

				<!-- Dots — right track -->
				<circle
					cx={RIGHT_X}
					cy={Y.amayaTech}
					r={DOT_R}
					fill="#1a2744"
					stroke="white"
					stroke-width="3"
				/>

				<!-- Dots — center track -->
				<circle
					cx={CENTER_X}
					cy={Y.merge}
					r={DOT_R}
					fill="#f59e0b"
					stroke="white"
					stroke-width="3"
				/>
				<circle
					cx={CENTER_X}
					cy={Y.electronLabs}
					r={DOT_R}
					fill="#1a2744"
					stroke="white"
					stroke-width="3"
				/>
				<circle
					cx={CENTER_X}
					cy={Y.split}
					r={DOT_R}
					fill="#f59e0b"
					stroke="white"
					stroke-width="3"
				/>

				<!-- Dots — split endpoints -->
				<circle
					cx={SPLIT_LEFT_X}
					cy={Y.splitEnd}
					r={DOT_R}
					fill="#94a3b8"
					stroke="white"
					stroke-width="3"
				/>
				<circle
					cx={SPLIT_RIGHT_X}
					cy={Y.splitEnd}
					r={DOT_R}
					fill="#f59e0b"
					stroke="white"
					stroke-width="3"
				/>

				<!-- Logos -->
				{#each desktopLogos as logo}
					<rect
						x={logo.x}
						y={logo.y}
						width={LOGO_BG}
						height={LOGO_BG}
						rx="6"
						fill="white"
						stroke="#e2e8f0"
						stroke-width="1"
					/>
					<image
						href={logo.src}
						x={logo.x + LOGO_PAD}
						y={logo.y + LOGO_PAD}
						width={LOGO_IMG}
						height={LOGO_IMG}
					/>
				{/each}

				<!-- Labels — left track (text to the left of dots) -->
				<text
					x={LEFT_X - 18}
					y={Y.brintonRes - 10}
					text-anchor="end"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					SEP 2009
				</text>
				<text
					x={LEFT_X - 18}
					y={Y.brintonRes + 8}
					text-anchor="end"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Brinton Research LLC
				</text>
				<text
					x={LEFT_X - 18}
					y={Y.brintonRes + 24}
					text-anchor="end"
					style="font-size: 11px; fill: #64748b"
				>
					EM field-solving CAD software
				</text>

				<text
					x={LEFT_X - 18}
					y={Y.brintonEng - 10}
					text-anchor="end"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					JUN 2010
				</text>
				<text
					x={LEFT_X - 18}
					y={Y.brintonEng + 8}
					text-anchor="end"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Brinton Engineering LLC
				</text>
				<text
					x={LEFT_X - 18}
					y={Y.brintonEng + 24}
					text-anchor="end"
					style="font-size: 11px; fill: #64748b"
				>
					EE consulting · Menlo Park, CA
				</text>

				<text
					x={LEFT_X - 18}
					y={Y.sigLabs - 10}
					text-anchor="end"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					NOV 2014
				</text>
				<text
					x={LEFT_X - 18}
					y={Y.sigLabs + 8}
					text-anchor="end"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Signal Laboratories, Inc.
				</text>
				<text
					x={LEFT_X - 18}
					y={Y.sigLabs + 24}
					text-anchor="end"
					style="font-size: 11px; fill: #64748b"
				>
					Wireless broadband · Fordable brand
				</text>

				<!-- Labels — right track (text to the right of dot + logo) -->
				<text
					x={RIGHT_X + LABEL_WITH_LOGO}
					y={Y.amayaTech - 10}
					text-anchor="start"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					NOV 2018
				</text>
				<text
					x={RIGHT_X + LABEL_WITH_LOGO}
					y={Y.amayaTech + 8}
					text-anchor="start"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Amaya Tech, Inc.
				</text>
				<text
					x={RIGHT_X + LABEL_WITH_LOGO}
					y={Y.amayaTech + 24}
					text-anchor="start"
					style="font-size: 11px; fill: #64748b"
				>
					EE consulting · California
				</text>

				<!-- Labels — center track (text to the right of dots) -->
				<text
					x={CENTER_X + 18}
					y={Y.merge - 10}
					text-anchor="start"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					2020
				</text>
				<text
					x={CENTER_X + 18}
					y={Y.merge + 8}
					text-anchor="start"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Siglabs Assets Acquired
				</text>
				<text
					x={CENTER_X + 18}
					y={Y.merge + 24}
					text-anchor="start"
					style="font-size: 11px; fill: #64748b"
				>
					Lineages reunited under Amaya Tech
				</text>

				<text
					x={CENTER_X + LABEL_WITH_LOGO}
					y={Y.electronLabs - 10}
					text-anchor="start"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					MAY 2021
				</text>
				<text
					x={CENTER_X + LABEL_WITH_LOGO}
					y={Y.electronLabs + 8}
					text-anchor="start"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					DBA "Electron Labs"
				</text>
				<text
					x={CENTER_X + LABEL_WITH_LOGO}
					y={Y.electronLabs + 24}
					text-anchor="start"
					style="font-size: 11px; fill: #64748b"
				>
					Fictitious business name filed
				</text>

				<text
					x={CENTER_X + 18}
					y={Y.split - 10}
					text-anchor="start"
					style="font-size: 11px; font-weight: 700; fill: #d97706; letter-spacing: 0.08em"
				>
					MAR 2026
				</text>
				<text
					x={CENTER_X + 18}
					y={Y.split + 8}
					text-anchor="start"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Company Split
				</text>
				<text
					x={CENTER_X + 18}
					y={Y.split + 24}
					text-anchor="start"
					style="font-size: 11px; fill: #64748b"
				>
					Restructured into two entities
				</text>

				<!-- Labels — split endpoints (centered below dots) -->
				<text
					x={SPLIT_LEFT_X}
					y={Y.splitEnd + 24}
					text-anchor="middle"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					Electron Labs
				</text>
				<text
					x={SPLIT_LEFT_X}
					y={Y.splitEnd + 42}
					text-anchor="middle"
					style="font-size: 12px; fill: #94a3b8"
				>
					(Sold)
				</text>

				<text
					x={SPLIT_RIGHT_X}
					y={Y.splitEnd + 24}
					text-anchor="middle"
					style="font-size: 14px; font-weight: 600; fill: #0f172a"
				>
					JDBC
				</text>
				<text
					x={SPLIT_RIGHT_X}
					y={Y.splitEnd + 42}
					text-anchor="middle"
					style="font-size: 12px; font-weight: 500; fill: #d97706"
				>
					(This company)
				</text>
			</svg>
		</div>

		<!-- Mobile timeline (simple vertical) -->
		<div class="mx-auto mt-16 max-w-2xl lg:hidden">
			<div class="relative ml-4 border-l-[2.5px] border-navy-200 pl-8">
				{#each entries as entry, i}
					<div class="relative pb-12 last:pb-0">
						<div
							class="absolute -left-[calc(2rem+1.25px)] top-0.5 flex h-[14px] w-[14px] items-center justify-center rounded-full border-[3px] border-white {entry.highlight
								? 'bg-amber-500'
								: 'bg-navy-800'}"
						></div>
						{#if entry.badge}
							<span
								class="mb-1.5 inline-block rounded-full px-2 py-0.5 text-[10px] font-semibold uppercase tracking-wider {entry.highlight
									? 'bg-amber-50 text-amber-700'
									: 'bg-slate-100 text-slate-500'}"
							>
								{entry.badge}
							</span>
						{/if}
						<span class="block text-xs font-bold uppercase tracking-widest text-accent-600">
							{entry.date}
						</span>
						<div class="mt-1 flex items-center gap-2">
							{#if entry.logos}
								{#each entry.logos as src}
									<img
										{src}
										alt=""
										class="h-6 w-6 rounded border border-slate-200 object-contain"
										width="24"
										height="24"
									/>
								{/each}
							{/if}
							<h3 class="text-base font-semibold text-slate-900">{entry.title}</h3>
						</div>
						<p class="mt-1.5 text-sm leading-relaxed text-slate-600">
							{entry.description}
						</p>
					</div>
				{/each}
			</div>

			<!-- Mobile split graphic -->
			<div class="mt-4 ml-4 pl-8">
				<svg viewBox="0 0 280 140" fill="none" class="w-full max-w-xs">
					<line x1="140" y1="0" x2="140" y2="30" stroke="#b3c2e0" stroke-width="2.5" />
					<path
						d="M 140 30 C 140 70, 60 70, 60 110"
						stroke="#b3c2e0"
						stroke-width="2.5"
						fill="none"
					/>
					<path
						d="M 140 30 C 140 70, 220 70, 220 110"
						stroke="#b3c2e0"
						stroke-width="2.5"
						fill="none"
					/>
					<circle cx="140" cy="30" r={DOT_R} fill="#f59e0b" stroke="white" stroke-width="3" />
					<circle cx="60" cy="110" r={DOT_R} fill="#94a3b8" stroke="white" stroke-width="3" />
					<circle cx="220" cy="110" r={DOT_R} fill="#f59e0b" stroke="white" stroke-width="3" />
					<text
						x="60"
						y="132"
						text-anchor="middle"
						style="font-size: 12px; font-weight: 600; fill: #0f172a"
					>
						Electron Labs
					</text>
					<text
						x="60"
						y="140"
						text-anchor="middle"
						style="font-size: 9px; fill: #94a3b8"
					>
					</text>
					<text
						x="220"
						y="132"
						text-anchor="middle"
						style="font-size: 12px; font-weight: 600; fill: #0f172a"
					>
						JDBC
					</text>
				</svg>
				<div class="mt-1 flex max-w-xs justify-between px-2 text-[10px] font-medium">
					<span class="text-slate-400">(Sold)</span>
					<span class="text-amber-600">(This company)</span>
				</div>
			</div>
		</div>

		<!-- Summary cards -->
		<div class="mx-auto mt-16 grid max-w-3xl gap-6 sm:grid-cols-2">
			<div class="rounded-xl border border-slate-200 bg-white p-6">
				<div class="flex items-center gap-3">
					<img
						src="/images/logos/electron-labs.png"
						alt="Electron Labs logo"
						class="h-10 w-10 rounded-lg border border-slate-200 object-contain"
						width="40"
						height="40"
					/>
					<h3 class="text-base font-semibold text-slate-900">Electron Labs</h3>
				</div>
				<p class="mt-3 text-sm leading-relaxed text-slate-600">
					The Electron Labs brand and associated business were sold as a separate entity during the
					March 2026 restructuring.
				</p>
				<span
					class="mt-3 inline-block rounded-full bg-slate-100 px-3 py-1 text-xs font-medium text-slate-500"
				>
					Sold
				</span>
			</div>

			<div class="rounded-xl border-2 border-accent-300 bg-white p-6 shadow-sm">
				<div class="flex items-center gap-3">
					<div class="flex h-10 w-10 items-center justify-center rounded-lg bg-accent-50">
						<svg viewBox="0 0 32 32" class="h-5 w-5" aria-hidden="true">
							<rect width="32" height="32" rx="6" fill="#111b30" />
							<path d="M18 4L10 18h6l-2 10 8-14h-6l2-10z" fill="#f59e0b" />
						</svg>
					</div>
					<h3 class="text-base font-semibold text-slate-900">JDBC</h3>
				</div>
				<p class="mt-3 text-sm leading-relaxed text-slate-600">
					JD Brinton Consulting, Inc. — the successor consulting practice, carrying forward the
					same leadership and engineering expertise.
				</p>
				<span
					class="mt-3 inline-block rounded-full bg-accent-50 px-3 py-1 text-xs font-medium text-accent-700"
				>
					This company
				</span>
			</div>
		</div>
	</div>
</section>

<Cta />
