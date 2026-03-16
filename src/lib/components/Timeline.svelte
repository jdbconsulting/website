<script lang="ts">
	const TRACK_W = 48;
	const PHOTO_SIZE = 200;
	const STAGGER = 220;
	const BRANCH_GAP = 30;
	const PHOTO_AREA_W = STAGGER + PHOTO_SIZE;
	const COMBINED_W = PHOTO_AREA_W + BRANCH_GAP + TRACK_W;
	const GAP = 30;

	const entries = [
		{
			year: '2005-2008 (Employee), 2009+ (Contractor)',
			offset: 72,
			title: 'Data Acquistion Engineer',
			org: 'XCOR Aerospace',
			description:
				'Employee: <ul class="list-disc ml-4"><li>EZ-Rocket (Long-EZ)</li><li>Rocket Racer (Velocity)</li><li>3M9 Lunar Descent Engine Program (NASA)</li><li>Lynx (XCOR)</li></ul>Contractor: <ul class="list-disc ml-4"><li>Designed bi-propellant high-voltage ignition system</li><li>Designed ground tie-down telemetry rack</li></ul>',
			image: '/images/timeline/xcor.jpg'
		},
		{
			year: '2006',
			offset: 25,
			title: 'Private Pilot Training',
			org: '',
			description:
				'~40 hours logged (no PPL).<br />CFI: <a href="https://en.wikipedia.org/wiki/Dick_Rutan" target="_blank" rel="noopener noreferrer">Dick Rutan</a><br />Aircraft: Long-EZ, Cherokee 180, Cessna 152, Citabria',
			image: '/images/timeline/pilot-training.jpg'
		},
		{
			year: '2008-2010 (Employee)',
			offset: 22,
			title: 'Avionics Electrical Engineer',
			org: 'SpaceX',
			description: '<ul class="list-disc ml-4"><li>Responsible Engineer for Falcon 9 Stage Controller and associated interface cards</li><li>Responsible Engineer for Remote I/O (RIO) Testbed</li><li>Frequent Waco test site debug engineer</li></ul>',
			image: '/images/timeline/spacex.jpg'
		},
		{
			year: '2010-2014 (Contractor)',
			offset: 68,
			title: 'Hardware Engineering Consultant',
			org: 'Astra Space (formerly Ventions, LLC)',
			description: 'Designed all vehicle electroncs<ul class="list-disc ml-4"><li>Power distribution board</li><li>Data acquistion board</li><li>Brushless DC motor board</li><li>Flight Termination System (FTS)</li><li>IMU board</li><li>Satellite radio board</li></ul>',
			image: '/images/timeline/ventions.jpg'
		},
		{
			year: '2014-2016 (Contractor)',
			offset: 28,
			title: 'Hardware Engineering Consultant',
			org: 'Motorola Mobility (acquired by Google ATAP)',
			description:
				'Lead HW Engineer for the Project Tango smartphone. Developed hardware using multiple 3D sensing technologies: <ul class="list-disc ml-4"><li>Stereo vision</li><li>IR projection</li><li>Time-of-Flight (ToF)</li><li>Stereo from motion</li></ul>',
			image: '/images/timeline/tango.jpg'
		},
		{
			year: '2016-2018',
			offset: 72,
			title: 'CEO',
			org: 'Signal Laboratories, Inc.',
			description: 'Bringing senior engineering expertise directly to ambitious teams.',
			image: '/images/timeline/siglabs.jpg'
		},
		{
			year: '2018-present',
			offset: 72,
			title: 'President',
			org: 'JD Brinton Consulting, Inc. <br />(Formerly Amaya Tech, Inc. DBA Electron Labs)',
			description: 'Bringing senior engineering expertise directly to ambitious teams.',
			image: ''
		},
		{
			year: '2022-2023',
			offset: 72,
			title: 'CTO',
			org: 'Red Leader Technologies, Inc.',
			description: 'Lead a small team that developed an ambitious high-performance LiDAR system.',
			image: '/images/timeline/redleader.jpg'
		},
		{
			year: '2023-present',
			offset: 72,
			title: 'Principal Avionics Hardware Engineer',
			org: 'Relativity Space',
			description: 'Working on the design and development of the Terran-R rocket.',
			image: ''
		}
	];

	let photoIdx = 0;
	const photoPositions: (null | 'near' | 'far')[] = entries.map((entry) => {
		if (!entry.image) return null;
		const pos: 'near' | 'far' = photoIdx % 2 === 0 ? 'near' : 'far';
		photoIdx++;
		return pos;
	});

	let measuredHeights: number[] = $state(entries.map(() => 160));

	const entryTops = $derived.by(() => {
		const tops: number[] = [];
		let cum = 0;
		for (let i = 0; i < measuredHeights.length; i++) {
			tops.push(cum);
			cum += measuredHeights[i] + GAP;
		}
		return tops;
	});

	const svgH = $derived(
		measuredHeights.reduce((sum, h) => sum + h, 0) + (measuredHeights.length - 1) * GAP
	);

	const trackDots = $derived(
		entries.map((e, i) => ({
			x: (e.offset / 100) * TRACK_W,
			y: entryTops[i] + measuredHeights[i] / 2
		}))
	);

	const desktopDots = $derived(
		trackDots.map((d) => ({
			x: PHOTO_AREA_W + BRANCH_GAP + d.x,
			y: d.y
		}))
	);

	function buildPath(dots: { x: number; y: number }[]): string {
		let d = `M ${dots[0].x} ${dots[0].y}`;
		for (let i = 1; i < dots.length; i++) {
			const prev = dots[i - 1];
			const curr = dots[i];
			const midY = (prev.y + curr.y) / 2;
			d += ` C ${prev.x} ${midY}, ${curr.x} ${midY}, ${curr.x} ${curr.y}`;
		}
		return d;
	}

	const mobileTrackPath = $derived(buildPath(trackDots));
	const desktopTrackPath = $derived(buildPath(desktopDots));

	const branches = $derived(
		entries.map((entry, i) => {
			const pos = photoPositions[i];
			if (!pos) return null;
			const dot = desktopDots[i];

			if (pos === 'near') {
				const endX = STAGGER + PHOTO_SIZE;
				return {
					path: `M ${dot.x} ${dot.y} C ${dot.x - 16} ${dot.y - 10}, ${endX + 14} ${dot.y + 8}, ${endX} ${dot.y}`,
					endX,
					endY: dot.y
				};
			} else {
				const endX = PHOTO_SIZE;
				const arc = i % 4 < 2 ? 1 : -1;
				return {
					path: `M ${dot.x} ${dot.y} C ${dot.x - 35} ${dot.y + 30 * arc}, ${endX + 40} ${dot.y - 24 * arc}, ${endX} ${dot.y}`,
					endX,
					endY: dot.y
				};
			}
		})
	);

	const photos = $derived(
		entries.map((entry, i) => {
			const pos = photoPositions[i];
			if (!pos) return null;
			return {
				x: pos === 'near' ? STAGGER : 0,
				y: trackDots[i].y - PHOTO_SIZE / 2,
				src: entry.image,
				alt: entry.title
			};
		})
	);
</script>

<section class="border-t border-slate-100 bg-slate-50 py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center lg:max-w-4xl">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
				A Lifetime in commercial aerospace and telecommunications
			</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-600">
				Two+ decades of engineering, from rockets to electron microscopes to wireless broadband.
			</p>
		</div>

		<div class="mx-auto mt-16 max-w-2xl lg:max-w-4xl">
			<div class="flex items-start">
				<div
					class="relative shrink-0 lg:hidden"
					style="width: {TRACK_W}px"
					aria-hidden="true"
				>
					<svg
						viewBox="0 0 {TRACK_W} {svgH}"
						fill="none"
						style="width: {TRACK_W}px; height: {svgH}px"
					>
						<path
							d={mobileTrackPath}
							stroke="#b3c2e0"
							stroke-width="2.5"
							stroke-linecap="round"
						/>
						{#each trackDots as dot, i}
							<circle
								cx={dot.x}
								cy={dot.y}
								r="7"
								fill={i === trackDots.length - 1 ? '#f59e0b' : '#1a2744'}
								stroke="white"
								stroke-width="3"
							/>
						{/each}
					</svg>
				</div>

				<div
					class="relative hidden shrink-0 lg:block"
					style="width: {COMBINED_W}px; height: {svgH}px"
					aria-hidden="true"
				>
					<svg
						viewBox="0 0 {COMBINED_W} {svgH}"
						fill="none"
						class="absolute inset-0"
						style="width: {COMBINED_W}px; height: {svgH}px"
					>
						{#each branches as branch}
							{#if branch}
								<path
									d={branch.path}
									stroke="#c8d5e8"
									stroke-width="2"
									stroke-linecap="round"
									fill="none"
								/>
								<circle cx={branch.endX} cy={branch.endY} r="3" fill="#c8d5e8" />
							{/if}
						{/each}
						<path
							d={desktopTrackPath}
							stroke="#b3c2e0"
							stroke-width="2.5"
							stroke-linecap="round"
						/>
						{#each desktopDots as dot, i}
							<circle
								cx={dot.x}
								cy={dot.y}
								r="7"
								fill={i === desktopDots.length - 1 ? '#f59e0b' : '#1a2744'}
								stroke="white"
								stroke-width="3"
							/>
						{/each}
					</svg>

					{#each photos as photo}
						{#if photo}
							<div
								class="absolute overflow-hidden rounded-xl border-2 border-white bg-slate-200 shadow-md"
								style="width: {PHOTO_SIZE}px; height: {PHOTO_SIZE}px; left: {photo.x}px; top: {photo.y}px"
							>
								<img
									src={photo.src}
									alt={photo.alt}
									class="h-full w-full object-cover"
									loading="lazy"
								/>
							</div>
						{/if}
					{/each}
				</div>

				<ol class="ml-6 flex flex-1 flex-col list-none sm:ml-8" style="gap: {GAP}px">
					{#each entries as entry, i}
						<li bind:clientHeight={measuredHeights[i]}>
							<span class="text-xs font-bold uppercase tracking-widest text-accent-600">
								{entry.year}
							</span>
							<h3 class="mt-1 text-base font-semibold text-slate-900">{entry.title}</h3>
							{#if entry.org}
								<p class="text-sm font-medium text-slate-500">{@html entry.org}</p>
							{/if}
							<p
								class="mt-1.5 text-sm leading-relaxed text-slate-600 [&_a]:font-medium [&_a]:text-navy-700 [&_a]:underline [&_a]:decoration-navy-300 [&_a]:transition-colors hover:[&_a]:text-accent-600 hover:[&_a]:decoration-accent-400"
							>
								{@html entry.description}
							</p>
						</li>
					{/each}
				</ol>
			</div>
		</div>
	</div>
</section>
