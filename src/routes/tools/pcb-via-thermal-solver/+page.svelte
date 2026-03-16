<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Hero from '$lib/components/Hero.svelte';

	const K_CU = 401;
	const K_AIR = 0.026;
	const MM_PER_CU_OZ = 0.0348;
	const MIN_LAYERS = 2;
	const MAX_LAYERS = 32;

	const mmToMil = (mm: number) => mm / 0.0254;
	const milToMm = (mil: number) => mil * 0.0254;
	const mmToOz = (mm: number) => mm / MM_PER_CU_OZ;
	const ozToMm = (oz: number) => oz * MM_PER_CU_OZ;
	const roundSig = (n: number) => (isFinite(n) ? parseFloat(n.toPrecision(8)) : 0);

	let boardThickness_mm = $state(1.5748);
	let kDielectric = $state(0.25);
	let copperLayers_mm: number[] = $state([0.0348, 0.0348]);
	let viaDrill_mm = $state(0.4);
	let viaPlatingEnabled = $state(true);
	let viaPlating_mm = $state(0.0254);
	let viaPitch_mm = $state(1);
	let viaFillEnabled = $state(true);
	let kFill = $state(3);
	let compW_mm = $state(8);
	let compL_mm = $state(8);
	let compQ = $state(10);

	let boardT_m = $derived(boardThickness_mm / 1000);
	let tCuTotal_m = $derived(copperLayers_mm.reduce((a, b) => a + b, 0) / 1000);
	let tDielectric_m = $derived(Math.max(boardT_m - tCuTotal_m, 0));
	let rSeries = $derived(
		tDielectric_m / Math.max(kDielectric, 1e-12) + tCuTotal_m / Math.max(K_CU, 1e-12)
	);
	let k1 = $derived(boardT_m / Math.max(rSeries, 1e-18));

	let rOuter_m = $derived(Math.max(viaDrill_mm / 2000, 0));
	let tPlate_m = $derived(viaPlatingEnabled ? Math.max(viaPlating_mm / 1000, 0) : 0);
	let rInner_m = $derived(Math.max(rOuter_m - tPlate_m, 0));
	let aCell = $derived(Math.max((viaPitch_mm / 1000) ** 2, 1e-18));
	let aPlating = $derived(
		viaPlatingEnabled ? Math.max(Math.PI * (rOuter_m ** 2 - rInner_m ** 2), 0) : 0
	);
	let aFill = $derived(viaFillEnabled ? Math.PI * rInner_m ** 2 : Math.PI * rOuter_m ** 2);

	let f2 = $derived(Math.min(aPlating / aCell, 1));
	let f3 = $derived(Math.min(aFill / aCell, 1));
	let f1 = $derived(Math.max(1 - f2 - f3, 0));
	let k3 = $derived(viaFillEnabled ? Math.max(kFill, 0) : K_AIR);
	let kEff = $derived(f1 * k1 + f2 * K_CU + f3 * k3);

	let compArea_m2 = $derived(Math.max((compW_mm / 1000) * (compL_mm / 1000), 1e-18));
	let deltaT = $derived(compQ * boardT_m / Math.max(kEff * compArea_m2, 1e-18));

	function addLayer() {
		if (copperLayers_mm.length >= MAX_LAYERS) return;
		copperLayers_mm = [...copperLayers_mm, 0.0348];
	}

	function removeLayer() {
		if (copperLayers_mm.length <= MIN_LAYERS) return;
		copperLayers_mm = copperLayers_mm.slice(0, -1);
	}

	const inputClass =
		'w-24 rounded-md border-slate-300 text-sm shadow-sm focus:border-accent-500 focus:ring-accent-500';
	const inputClassDisabled =
		'w-24 rounded-md border-slate-200 bg-slate-100 text-sm text-slate-400 shadow-sm';
	const inputClassNarrow =
		'w-20 rounded-md border-slate-300 text-sm shadow-sm focus:border-accent-500 focus:ring-accent-500';
	const inputClassNarrowDisabled =
		'w-20 rounded-md border-slate-200 bg-slate-100 text-sm text-slate-400 shadow-sm';

	let explanationOpen = $state(false);
</script>

{#snippet mmMilInput(label: string, value: number, onchange: (v: number) => void, disabled?: boolean)}
	<div class="flex flex-wrap items-center gap-x-3 gap-y-1 py-1.5">
		<span class="min-w-44 text-sm font-medium text-slate-700">{label}</span>
		<div class="flex items-center gap-1.5">
			<input
				type="number"
				step="any"
				{value}
				{disabled}
				oninput={(e) => onchange(parseFloat(e.currentTarget.value) || 0)}
				class={disabled ? inputClassDisabled : inputClass}
			/>
			<span class="text-xs text-slate-500">mm</span>
		</div>
		<div class="flex items-center gap-1.5">
			<input
				type="number"
				step="any"
				value={roundSig(mmToMil(value))}
				{disabled}
				oninput={(e) => onchange(milToMm(parseFloat(e.currentTarget.value) || 0))}
				class={disabled ? inputClassDisabled : inputClass}
			/>
			<span class="text-xs text-slate-500">mil</span>
		</div>
	</div>
{/snippet}

{#snippet mmMilOzInput(label: string, value: number, onchange: (v: number) => void)}
	<div class="flex flex-wrap items-center gap-x-3 gap-y-1 py-1.5">
		<span class="min-w-44 text-sm font-medium text-slate-700">{label}</span>
		<div class="flex items-center gap-1.5">
			<input
				type="number"
				step="any"
				{value}
				oninput={(e) => onchange(parseFloat(e.currentTarget.value) || 0)}
				class={inputClassNarrow}
			/>
			<span class="text-xs text-slate-500">mm</span>
		</div>
		<div class="flex items-center gap-1.5">
			<input
				type="number"
				step="any"
				value={roundSig(mmToMil(value))}
				oninput={(e) => onchange(milToMm(parseFloat(e.currentTarget.value) || 0))}
				class={inputClassNarrow}
			/>
			<span class="text-xs text-slate-500">mil</span>
		</div>
		<div class="flex items-center gap-1.5">
			<input
				type="number"
				step="any"
				value={roundSig(mmToOz(value))}
				oninput={(e) => onchange(ozToMm(parseFloat(e.currentTarget.value) || 0))}
				class={inputClassNarrow}
			/>
			<span class="text-xs text-slate-500">oz</span>
		</div>
	</div>
{/snippet}

{#snippet resultRow(label: string, value: string, highlight?: boolean)}
	<div class="flex items-baseline justify-between gap-4 py-1.5">
		<span class="text-sm text-slate-600">{label}</span>
		<span class={highlight ? 'text-lg font-bold text-accent-600' : 'text-sm font-semibold text-slate-900'}>{value}</span>
	</div>
{/snippet}

<Seo
	title="PCB Via-Stitching Vertical Thermal Solver"
	description="Calculate effective through-plane thermal conductivity for PCB via-stitching patterns. Free online tool for thermal management of high-power components."
/>

<Hero
	title="PCB Via-Stitching Thermal Solver"
	subtitle="Calculate the effective vertical thermal conductivity through a PCB stackup with via stitching, and estimate temperature rise for a given heat load."
	compact
/>

<section class="bg-white py-12 sm:py-16">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="grid gap-8 lg:grid-cols-5">
			<!-- Inputs -->
			<div class="space-y-6 lg:col-span-3">
				<!-- PCB Geometry & Materials -->
				<div class="rounded-2xl border border-slate-200 p-6">
					<h2 class="text-lg font-semibold text-slate-900">PCB Geometry &amp; Materials</h2>
					<div class="mt-4 border-t border-slate-100 pt-4">
						<div class="flex items-center gap-3 pb-3">
							<span class="min-w-44 text-sm font-medium text-slate-700">Copper layers</span>
							<button
								onclick={removeLayer}
								disabled={copperLayers_mm.length <= MIN_LAYERS}
								class="rounded-md bg-slate-100 px-3 py-1 text-sm font-medium text-slate-700 transition-colors hover:bg-slate-200 disabled:cursor-not-allowed disabled:opacity-40"
							>
								&minus; Layer
							</button>
							<span class="min-w-6 text-center text-sm font-semibold text-slate-900">
								{copperLayers_mm.length}
							</span>
							<button
								onclick={addLayer}
								disabled={copperLayers_mm.length >= MAX_LAYERS}
								class="rounded-md bg-slate-100 px-3 py-1 text-sm font-medium text-slate-700 transition-colors hover:bg-slate-200 disabled:cursor-not-allowed disabled:opacity-40"
							>
								+ Layer
							</button>
						</div>

						{#each copperLayers_mm as _, i}
							{@render mmMilOzInput(
								`Copper thickness L${i + 1}`,
								copperLayers_mm[i],
								(v) => (copperLayers_mm[i] = v)
							)}
						{/each}

						{@render mmMilInput(
							'Total PCB thickness',
							boardThickness_mm,
							(v) => (boardThickness_mm = v)
						)}

						<div class="flex flex-wrap items-center gap-x-3 gap-y-1 py-1.5">
							<span class="min-w-44 text-sm font-medium text-slate-700">
								Dielectric thermal conductivity
							</span>
							<div class="flex items-center gap-1.5">
								<input
									type="number"
									step="any"
									bind:value={kDielectric}
									class={inputClass}
								/>
								<span class="text-xs text-slate-500">W/m&middot;K</span>
							</div>
						</div>
					</div>
				</div>

				<!-- Via Parameters -->
				<div class="rounded-2xl border border-slate-200 p-6">
					<h2 class="text-lg font-semibold text-slate-900">Via Parameters</h2>
					<div class="mt-4 border-t border-slate-100 pt-4">
						{@render mmMilInput('Via drill size', viaDrill_mm, (v) => (viaDrill_mm = v))}

						<div class="flex items-center gap-x-3 py-1.5">
							<span class="min-w-44 text-sm font-medium text-slate-700">Via plating enabled</span>
							<input
								type="checkbox"
								bind:checked={viaPlatingEnabled}
								class="h-4 w-4 rounded border-slate-300 text-accent-500 focus:ring-accent-500"
							/>
						</div>

						{@render mmMilInput(
							'Via plating thickness',
							viaPlating_mm,
							(v) => (viaPlating_mm = v),
							!viaPlatingEnabled
						)}

						{@render mmMilInput('Via stitching pitch', viaPitch_mm, (v) => (viaPitch_mm = v))}

						<div class="flex items-center gap-x-3 py-1.5">
							<span class="min-w-44 text-sm font-medium text-slate-700">Via fill enabled</span>
							<input
								type="checkbox"
								bind:checked={viaFillEnabled}
								class="h-4 w-4 rounded border-slate-300 text-accent-500 focus:ring-accent-500"
							/>
						</div>

						<div class="flex flex-wrap items-center gap-x-3 gap-y-1 py-1.5">
							<span class="min-w-44 text-sm font-medium text-slate-700">
								Via fill thermal conductivity
							</span>
							<div class="flex items-center gap-1.5">
								<input
									type="number"
									step="any"
									bind:value={kFill}
									disabled={!viaFillEnabled}
									class={viaFillEnabled ? inputClass : inputClassDisabled}
								/>
								<span class="text-xs text-slate-500">W/m&middot;K</span>
							</div>
						</div>
					</div>
				</div>

				<!-- Component & Heat Load -->
				<div class="rounded-2xl border border-slate-200 p-6">
					<h2 class="text-lg font-semibold text-slate-900">Component &amp; Heat Load</h2>
					<div class="mt-4 border-t border-slate-100 pt-4">
						{@render mmMilInput('Component width', compW_mm, (v) => (compW_mm = v))}
						{@render mmMilInput('Component length', compL_mm, (v) => (compL_mm = v))}

						<div class="flex flex-wrap items-center gap-x-3 gap-y-1 py-1.5">
							<span class="min-w-44 text-sm font-medium text-slate-700">Heat dissipation</span>
							<div class="flex items-center gap-1.5">
								<input
									type="number"
									step="any"
									bind:value={compQ}
									class={inputClass}
								/>
								<span class="text-xs text-slate-500">W</span>
							</div>
						</div>
					</div>
				</div>
			</div>

			<!-- Results (sticky sidebar) -->
			<div class="lg:col-span-2">
				<div class="sticky top-24 space-y-6">
					<div class="rounded-2xl border border-slate-200 bg-white p-4">
						<img
							src="/images/tools/via-stitching-thermal/model.png"
							alt="PCB cross-section model showing via stitching with plating and fill regions"
							class="w-full rounded-lg"
						/>
					</div>

					<div class="rounded-2xl border border-slate-200 bg-slate-50 p-6">
						<h2 class="text-lg font-semibold text-slate-900">Effective Through-Plane Conductivity</h2>
						<div class="mt-4 space-y-0.5 border-t border-slate-200 pt-4">
							{@render resultRow(
								'Computed dielectric thickness',
								`${(tDielectric_m * 1000).toFixed(4)} mm (${mmToMil(tDielectric_m * 1000).toFixed(2)} mil)`
							)}
							<div class="my-2 border-t border-slate-200"></div>
							{@render resultRow('Region 1 k (PCB stackup)', `${k1.toFixed(3)} W/m·K`)}
							{@render resultRow('Region 2 k (via plating)', `${K_CU.toFixed(1)} W/m·K`)}
							{@render resultRow('Region 3 k (via fill/void)', `${k3.toFixed(3)} W/m·K`)}
							<div class="my-2 border-t border-slate-200"></div>
							{@render resultRow('Area fraction Region 1', `${(f1 * 100).toFixed(3)}%`)}
							{@render resultRow('Area fraction Region 2', `${(f2 * 100).toFixed(3)}%`)}
							{@render resultRow('Area fraction Region 3', `${(f3 * 100).toFixed(3)}%`)}
							<div class="my-2 border-t border-slate-200"></div>
							{@render resultRow('Total effective k_through', `${kEff.toFixed(3)} W/m·K`, true)}
						</div>
					</div>

					<div class="rounded-2xl border border-accent-200 bg-accent-50 p-6">
						<h2 class="text-lg font-semibold text-slate-900">PCB Temperature Rise</h2>
						<div class="mt-4 border-t border-accent-200 pt-4">
							<div class="flex items-baseline justify-between gap-4">
								<span class="text-sm text-slate-600">&Delta;T across PCB</span>
								<span class="text-2xl font-bold text-accent-600">
									{deltaT.toFixed(3)} K
								</span>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Explanation Section -->
<section class="border-t border-slate-100 bg-slate-50 py-16 sm:py-20">
	<div class="mx-auto max-w-4xl px-4 sm:px-6 lg:px-8">
		<button
			onclick={() => (explanationOpen = !explanationOpen)}
			class="flex w-full items-center justify-between"
		>
			<h2 class="text-2xl font-bold tracking-tight text-slate-900">How This Thermal Solver Works</h2>
			<svg
				class="h-6 w-6 shrink-0 text-slate-500 transition-transform {explanationOpen ? 'rotate-180' : ''}"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
				stroke-width="2"
			>
				<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
			</svg>
		</button>

		{#if explanationOpen}
			<div class="prose prose-slate mt-8 max-w-none prose-headings:text-slate-900 prose-h3:text-accent-600">
				<h3>Overview</h3>
				<p>
					This solver calculates the effective thermal conductivity through a PCB stackup with via
					stitching, helping you understand how heat flows vertically through your board design.
					It's particularly useful for thermal management of high-power components.
				</p>

				<h3>What the Solver Calculates</h3>
				<p>The tool performs a <strong>three-region thermal analysis</strong> of your PCB:</p>
				<ul>
					<li><strong>Region 1:</strong> The PCB stackup (dielectric layers + copper layers)</li>
					<li>
						<strong>Region 2:</strong> Via plating (copper barrel around the drilled hole)
					</li>
					<li><strong>Region 3:</strong> Via fill/void (the material inside the via)</li>
				</ul>

				<h3>Step-by-Step Calculation Process</h3>

				<h4>1. PCB Stackup Analysis</h4>
				<p>The solver first calculates the thermal resistance of your PCB stackup:</p>
				<ul>
					<li>Determines total copper thickness from all layers</li>
					<li>
						Calculates remaining dielectric thickness (total PCB thickness &minus; copper thickness)
					</li>
					<li>
						Computes thermal resistance: R = (dielectric_thickness / k_dielectric) +
						(copper_thickness / k_copper)
					</li>
					<li>Converts to thermal conductivity: k&#8321; = board_thickness / R</li>
				</ul>

				<h4>2. Via Geometry Analysis</h4>
				<p>For each via in your stitching pattern:</p>
				<ul>
					<li>Calculates outer radius (drill diameter &divide; 2)</li>
					<li>Calculates inner radius (outer radius &minus; plating thickness)</li>
					<li>Determines cross-sectional areas for each region</li>
				</ul>

				<h4>3. Area Fraction Calculations</h4>
				<p>
					The solver determines what percentage of the via pitch area is occupied by each region:
				</p>
				<ul>
					<li><strong>f&#8321; (Region 1):</strong> PCB stackup area fraction</li>
					<li><strong>f&#8322; (Region 2):</strong> Via plating area fraction</li>
					<li><strong>f&#8323; (Region 3):</strong> Via fill/void area fraction</li>
				</ul>
				<p>These fractions must sum to 1.0 (100% of the area).</p>

				<h4>4. Effective Thermal Conductivity</h4>
				<p>
					The final effective thermal conductivity is calculated using a <strong
						>parallel thermal resistance model</strong
					>:
				</p>
				<p>
					<strong>k_effective = f&#8321; &times; k&#8321; + f&#8322; &times; k&#8322; + f&#8323; &times; k&#8323;</strong>
				</p>
				<p>Where:</p>
				<ul>
					<li>k&#8321; = PCB stackup thermal conductivity</li>
					<li>k&#8322; = Copper thermal conductivity (401 W/m&middot;K)</li>
					<li>k&#8323; = Via fill thermal conductivity (or air if unfilled)</li>
				</ul>

				<h4>5. Temperature Rise Calculation</h4>
				<p>
					For a given component heat load, the solver calculates the temperature rise across the
					PCB:
				</p>
				<p>
					<strong
						>&Delta;T = Q &times; board_thickness / (k_effective &times; component_area)</strong
					>
				</p>
				<p>Where Q is the heat load in watts and component_area is width &times; length.</p>

				<h3>Key Assumptions</h3>
				<ul>
					<li>
						<strong>One-dimensional heat flow:</strong> Heat flows only vertically through the PCB
					</li>
					<li><strong>Steady-state conditions:</strong> No transient thermal effects</li>
					<li>
						<strong>Uniform via distribution:</strong> Vias are evenly spaced in a regular pattern
					</li>
					<li>
						<strong>Perfect thermal contact:</strong> No thermal resistance at material interfaces
					</li>
					<li>
						<strong>Isotropic materials:</strong> Thermal conductivity is the same in all directions
					</li>
				</ul>

				<h3>When to Use This Tool</h3>
				<ul>
					<li>Designing thermal vias for high-power components</li>
					<li>Optimizing via stitching patterns for thermal management</li>
					<li>Comparing different via fill materials</li>
					<li>Estimating temperature rise across PCB thickness</li>
					<li>Validating thermal design before prototyping</li>
				</ul>

				<h3>Limitations</h3>
				<ul>
					<li>Does not account for lateral heat spreading</li>
					<li>Assumes uniform temperature across component area</li>
					<li>Does not include convection or radiation effects</li>
					<li>Simplified via geometry (cylindrical vias only)</li>
					<li>No consideration of thermal vias under components vs. in between</li>
				</ul>

				<h3>Interpreting Results</h3>
				<p>
					<strong>Higher k_effective values</strong> indicate better thermal conductivity through the
					PCB, meaning lower temperature rise for the same heat load and more effective heat sinking to
					the opposite side of the board.
				</p>
				<p>
					<strong>Lower &Delta;T values</strong> are better, indicating less temperature rise across the
					PCB thickness.
				</p>
			</div>
		{/if}
	</div>
</section>
