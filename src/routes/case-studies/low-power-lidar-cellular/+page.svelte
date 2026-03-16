<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Cta from '$lib/components/Cta.svelte';
</script>

<Seo
	title="Low-Powered Lidar With Cellular Backhaul"
	description="Case study: Designing a solar/battery-powered remote sensing platform with LIDAR, an STM32F7 MCU, and 3G cellular backhaul for multi-year unattended operation."
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
				>Embedded Systems &amp; IoT</span
			>
		</div>
		<h1 class="mt-4 max-w-4xl text-4xl font-bold tracking-tight text-white sm:text-5xl">
			Low-Powered Lidar With Cellular Backhaul
		</h1>
		<p class="mt-6 max-w-2xl text-lg leading-relaxed text-slate-300">
			A solar and battery-powered remote sensing platform built around an STM32F7 MCU, designed for
			multi-year unattended operation with 3G cellular uplink.
		</p>
		<div class="mt-8">
			<a
				href="https://github.com/jdbrinton/bigpine-remote-camera"
				target="_blank"
				rel="noopener noreferrer"
				class="inline-flex items-center gap-2 rounded-full bg-white/10 px-4 py-2 text-sm font-medium text-white transition-colors hover:bg-white/20"
			>
				<svg class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
					<path
						fill-rule="evenodd"
						d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
						clip-rule="evenodd"
					/>
				</svg>
				View on GitHub
			</a>
		</div>
	</div>
</section>

<article class="bg-white py-16 sm:py-20">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-3xl">
			<div class="grid gap-6 rounded-2xl border border-slate-200 bg-slate-50 p-6 sm:grid-cols-3">
				<div>
					<div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Domain</div>
					<div class="mt-1 text-sm font-medium text-slate-900">Remote Sensing &amp; IoT</div>
				</div>
				<div>
					<div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Duration</div>
					<div class="mt-1 text-sm font-medium text-slate-900">16 weeks</div>
				</div>
				<div>
					<div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Key Result</div>
					<div class="mt-1 text-sm font-medium text-accent-600">3-Year Battery Life</div>
				</div>
			</div>

			<img
				src="/images/case-studies/low-power-lidar-cellular/hero.jpg"
				alt="Assembled remote sensing platform with solar panel and cellular antenna"
				class="mt-12 w-full rounded-2xl"
			/>

			<div class="prose prose-slate mt-12 max-w-none prose-headings:font-semibold prose-headings:tracking-tight prose-a:text-accent-600 prose-a:no-underline hover:prose-a:underline">
				<h2>The Challenge</h2>
				<p>
					A client needed a remote sensing platform that could operate unattended in off-grid
					environments for years at a time. The system had to capture LIDAR range data and camera
					imagery, then backhaul the data over a cellular link — all while running on a small
					primary-cell battery supplemented by a solar panel. Every microwatt mattered.
				</p>
				<p>
					Commercial off-the-shelf solutions either consumed too much power for multi-year
					operation or lacked the sensor flexibility the application demanded. A custom hardware
					and firmware platform was the only path forward.
				</p>

				<h2>Our Approach</h2>

				<h3>System Architecture</h3>
				<p>
					We designed a two-board system — a main board and a camera/sensor board — connected via
					FPC cables. The main board carries the STM32F7 microcontroller, a SIM7100A 3G cellular
					modem, SD card storage, a peak-power solar tracker, supercapacitor-backed sleep
					circuitry, and interfaces for pan/tilt servos and a LIDAR module. The camera board hosts
					an ArduCam module for low-frame-rate image capture.
				</p>

				<img
					src="/images/case-studies/low-power-lidar-cellular/block-diagram.jpg"
					alt="System block diagram showing MCU, modem, sensors, and power architecture"
					class="rounded-xl"
				/>

				<h3>Ultra-Low-Power Design</h3>
				<p>
					The power budget was the single hardest constraint. At 24 captures per day on a
					100 W·hr primary cell, the system needed to last three years — meaning average
					power draw had to stay well below 4 mW.
				</p>
				<p>
					To achieve this, all switching regulators can be fully shut down between capture
					events. A supercapacitor keeps only the MCU's RTC and an onboard IMU alive during
					deep sleep, enabling both timed wake-up and motion-interrupt wake-up. The modem —
					by far the largest power consumer — boots only a few times per day; photos are cached
					to the SD card in the meantime to minimize cellular on-time.
				</p>

				<img
					src="/images/case-studies/low-power-lidar-cellular/main-board.jpg"
					alt="Main PCB front side showing STM32F7, modem, and power management circuitry"
					class="rounded-xl"
				/>

				<h3>Hardware Design</h3>
				<p>
					Both boards were designed from schematic through layout in-house. The main board
					integrates a complex power tree — solar input with MPPT, battery charging, supercap
					management, and multiple switchable rails — alongside high-speed digital interfaces
					for the modem and SD card. The camera board keeps the optical path short and isolated
					from digital noise.
				</p>

				<img
					src="/images/case-studies/low-power-lidar-cellular/camera-board.jpg"
					alt="Camera board PCB layout"
					class="rounded-xl"
				/>

				<h3>Firmware</h3>
				<p>
					Firmware was developed in C/C++ on the STM32 HAL. The architecture is
					event-driven: the MCU wakes on an RTC alarm or IMU interrupt, powers up the
					necessary peripherals, captures and stores data, and optionally initiates a modem
					session to upload cached payloads. Each wake cycle is profiled to stay within
					a strict energy envelope.
				</p>

				<h2>Results</h2>
				<ul>
					<li>
						<strong>3+ year projected battery life</strong> on a single 100 W·hr primary
						cell at 24 captures per day, validated by bench power profiling
					</li>
					<li>
						<strong>Sub-second wake-to-capture latency</strong>, ensuring the system
						doesn't miss transient events triggered by the IMU
					</li>
					<li>
						<strong>Reliable 3G backhaul</strong> via the SIM7100A modem with automatic
						retry and SD-card spooling for coverage gaps
					</li>
					<li>
						<strong>Modular sensor interface</strong> supporting LIDAR, ArduCam, and
						pan/tilt servos over a single FPC interconnect
					</li>
				</ul>

				<h2>Technical Highlights</h2>
				<ul>
					<li>
						Peak-power solar tracker extends effective battery life significantly in
						deployments with even partial sun exposure
					</li>
					<li>
						Supercapacitor-backed sleep domain eliminates regulator quiescent draw,
						dropping sleep-mode consumption to the low-microamp range
					</li>
					<li>
						SD card caching decouples capture rate from modem uplink schedule, allowing
						burst uploads that amortize the modem's high boot-up energy cost
					</li>
					<li>
						The design is <a href="https://github.com/jdbrinton/bigpine-remote-camera">open-source</a>,
						including schematics, PCB layout, and proof-of-concept firmware
					</li>
				</ul>

				<h2>Client Impact</h2>
				<p>
					The platform gave the client a flexible, field-proven foundation for remote
					environmental monitoring. Because the hardware and firmware are open-source, their
					internal engineering team can extend sensor support and tune the power profile for
					new deployment scenarios without vendor lock-in.
				</p>
			</div>
		</div>
	</div>
</article>

<Cta
	heading="Need a Custom Remote Sensing Platform?"
	body="We design ultra-low-power embedded systems that operate unattended for years."
	buttonText="Start a Conversation"
/>
