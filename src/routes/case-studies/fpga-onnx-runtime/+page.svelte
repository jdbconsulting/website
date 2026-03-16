<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Cta from '$lib/components/Cta.svelte';
</script>

<Seo
	title="FPGA Based ONNX Runtime Hardware"
	description="Case study: Designing a custom FPGA accelerator for ONNX Runtime inference for optimization with random matrix multiplication."
/>

<section class="relative overflow-hidden bg-navy-950">
	<div
		class="absolute inset-0 bg-[radial-gradient(ellipse_at_top_right,rgba(59,130,246,0.12),transparent_60%)]"
		aria-hidden="true"
	></div>
	<div class="relative mx-auto max-w-7xl px-4 py-16 sm:px-6 sm:py-20 lg:px-8 lg:py-24">
		<a
			href="/case-studies"
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
				<path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18" />
			</svg>
			All Case Studies
		</a>
		<div class="mt-6 flex items-center gap-3">
			<span class="rounded-full bg-white/10 px-3 py-1 text-xs font-medium text-accent-400"
				>FPGA &amp; ML Acceleration</span
			>
		</div>
		<h1 class="mt-4 max-w-4xl text-4xl font-bold tracking-tight text-white sm:text-5xl">
			FPGA Based ONNX Runtime Hardware
		</h1>
		<p class="mt-6 max-w-2xl text-lg leading-relaxed text-slate-300">
			Designing a custom FPGA execution provider for the ONNX Runtime — enabling hardware,
			optimized for Approximate Matrix Multiplication (AMM).
		</p>
	</div>
</section>

<article class="bg-white py-16 sm:py-20">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-3xl">
			<div class="grid gap-6 rounded-2xl border border-slate-200 bg-slate-50 p-6 sm:grid-cols-3">
				<div>
					<div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Domain</div>
					<div class="mt-1 text-sm font-medium text-slate-900">High Performance Computing</div>
				</div>
				<div>
					<div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Duration</div>
					<div class="mt-1 text-sm font-medium text-slate-900">24 weeks</div>
				</div>
				<div>
					<div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Key Result</div>
					<div class="mt-1 text-sm font-medium text-accent-600">Specialized HW Accelerator</div>
				</div>
			</div>
			<div class="mb-12"></div>
			<img
				src="/images/case-studies/fpga-onnx-runtime/hero.jpg"
				alt="FPGA development board used for ONNX Runtime acceleration"
				class="mb-12 w-full rounded-2xl"
			/>
			<div class="prose prose-slate mt-12 max-w-none prose-headings:font-semibold prose-headings:tracking-tight prose-a:text-accent-600 prose-a:no-underline hover:prose-a:underline">
				<h2>The Challenge</h2>
				<p>
					At the turn of the AI explosion, many hardware companies were trying innovative approaches
					to solving LLM workloads. Here at JDBC, we adopted a novel approach to solving LLM workloads
					using Approximate Matrix Multiplication (AMM). These type of operations are not conducive to
					GPU-based approaches since the random access nature of the operation causes most caches to 
					be invalidated. We knew that new hardware would be needed to solve this problem and we started
					with an FPGA-based approach to validate the concept.
				</p>
				<p>
					The ONNX Runtime by Microsoft is a open-source library for running machine learning models on
					a variety of hardware platforms. We identified it as a good fit for our approach and we started
					by building a custom execution provider for the ONNX Runtime.
				</p>
				<h2>Our Approach</h2>
				<h3>The Memory Bottleneck</h3>
				<p>
					Besides being in short supply, non-HBM high-performance DRAM has very high power-consumption.
					Settling on DDR3, we identified a novel memory bus architecture which reduced power consumption
					and improved throughput by using a fly-by topology with over 100 drops. Signal integrity was
					achieved with exquisitly detailed simulations, layout, and fabrication binning.
				</p>
				<p>
					Further, power consumption was reduced on the data bus with electrically short routing and weak
					termination. Power consumption rivaled that of HBM. To reduce costs, Efinix Titanium FPGAs were used.
				</p>

				<img
					src="/images/case-studies/fpga-onnx-runtime/memory-topology.jpg"
					alt="DDR3 fly-by memory bus topology layout"
					class="rounded-xl"
				/>

				<h3>Custom Execution Provider Architecture</h3>
				<p>
					We developed a custom ONNX Runtime execution provider over ethernet that could execute
					arbitrary ONNX models, including the latest LLM models such as Llama. While moving data to the
					accelerator card was slow, it only had to be done when the weights were changed. This architecture
					enabled ultra low-cost hardware.
				</p>

				<img
					src="/images/case-studies/fpga-onnx-runtime/architecture.jpg"
					alt="ONNX Runtime execution provider architecture diagram"
					class="rounded-xl"
				/>



				<h2>Results</h2>
				<p>
					While the PCB was completed, simulation showed the Approximate Matrix Multiplication (AMM)
					algorithm was too noisy for LLM workloads, and the HPC landscape became even more
					competitive, so we opted to cancel the project. However, many lessons were learned.
				</p>
			</div>
		</div>
	</div>
</article>

<Cta
	heading="Facing a Similar Challenge?"
	body="We help teams push ML inference to the edge with custom hardware acceleration."
	buttonText="Start a Conversation"
/>
