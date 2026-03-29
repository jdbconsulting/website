<script lang="ts">
	import { page } from '$app/state';

	let menuOpen = $state(false);
	let aboutDropdownOpen = $state(false);
	let toolsDropdownOpen = $state(false);
	let caseStudiesDropdownOpen = $state(false);
	let mobileAboutOpen = $state(false);
	let mobileToolsOpen = $state(false);
	let mobileCaseStudiesOpen = $state(false);

	const links = [{ href: '/', label: 'Home' }];

	const aboutLinks = [
		{ href: '/about/history', label: 'History' },
		{ href: '/about/joel-brinton', label: 'Joel Brinton', separator: 'People' }
	];

	const caseStudyLinks = [
		{ href: '/case-studies/fpga-onnx-runtime', label: 'FPGA Based ONNX Runtime Hardware' },
		{ href: '/case-studies/low-power-lidar-cellular', label: 'Low-Powered Lidar With Cellular Backhaul' }
	];

	const toolLinks = [
		{ href: '/tools/pcb-via-thermal-solver', label: 'PCB Via Thermal Solver' }
	];

	function isActive(href: string): boolean {
		if (href === '/') return page.url.pathname === '/';
		return page.url.pathname.startsWith(href);
	}
</script>

<header class="sticky top-0 z-50 border-b border-slate-200/80 bg-white/95 backdrop-blur-md">
	<nav
		class="mx-auto flex max-w-7xl items-center justify-between px-4 sm:px-6 lg:px-8"
		aria-label="Main navigation"
	>
		<a href="/" class="flex items-center gap-2.5 py-4">
			<svg viewBox="0 0 32 32" class="h-8 w-8" aria-hidden="true">
				<rect width="32" height="32" rx="6" fill="#111b30" />
				<path d="M18 4L10 18h6l-2 10 8-14h-6l2-10z" fill="#f59e0b" />
			</svg>
			<div class="flex flex-col">
				<span class="text-lg font-bold leading-tight tracking-tight text-slate-900">JDBC</span>
				<span class="text-[10px] leading-tight text-slate-500">JD Brinton Consulting, Inc.</span>
			</div>
		</a>

		<div class="hidden items-center gap-1 md:flex">
			{#each links as link}
				<a
					href={link.href}
					class="rounded-md px-3 py-2 text-sm font-medium transition-colors
						{isActive(link.href)
						? 'bg-slate-100 text-navy-700'
						: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
					aria-current={isActive(link.href) ? 'page' : undefined}
				>
					{link.label}
				</a>
			{/each}

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			class="relative"
			onmouseenter={() => (aboutDropdownOpen = true)}
			onmouseleave={() => (aboutDropdownOpen = false)}
		>
			<a
				href="/about"
				class="inline-flex items-center gap-1 rounded-md px-3 py-2 text-sm font-medium transition-colors
					{isActive('/about')
					? 'bg-slate-100 text-navy-700'
					: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
				aria-current={isActive('/about') ? 'page' : undefined}
			>
				About
				<svg
					class="h-4 w-4 transition-transform {aboutDropdownOpen ? 'rotate-180' : ''}"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
				>
					<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
				</svg>
			</a>
			{#if aboutDropdownOpen}
				<div class="absolute left-0 top-full z-50 w-56 pt-2">
				<div
					class="rounded-lg border border-slate-200 bg-white py-1 shadow-lg"
				>
					{#each aboutLinks as link}
						{#if link.separator}
							<div class="mx-3 my-1 border-t border-slate-100"></div>
							<span class="block px-4 pt-1.5 pb-0.5 text-[10px] font-semibold uppercase tracking-wider text-slate-400">{link.separator}</span>
						{/if}
						<a
							href={link.href}
							class="block px-4 py-2.5 text-sm text-slate-600 transition-colors hover:bg-slate-50 hover:text-slate-900"
							onclick={() => (aboutDropdownOpen = false)}
						>
							{link.label}
						</a>
					{/each}
				</div>
				</div>
			{/if}
		</div>

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			class="relative"
			onmouseenter={() => (caseStudiesDropdownOpen = true)}
			onmouseleave={() => (caseStudiesDropdownOpen = false)}
		>
			<a
				href="/case-studies"
				class="inline-flex items-center gap-1 rounded-md px-3 py-2 text-sm font-medium transition-colors
					{isActive('/case-studies')
					? 'bg-slate-100 text-navy-700'
					: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
				aria-current={isActive('/case-studies') ? 'page' : undefined}
			>
				Case Studies
				<svg
					class="h-4 w-4 transition-transform {caseStudiesDropdownOpen ? 'rotate-180' : ''}"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
				>
					<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
				</svg>
			</a>
			{#if caseStudiesDropdownOpen}
				<div class="absolute left-0 top-full z-50 w-72 pt-2">
				<div
					class="rounded-lg border border-slate-200 bg-white py-1 shadow-lg"
				>
					{#each caseStudyLinks as study}
						<a
							href={study.href}
							class="block px-4 py-2.5 text-sm text-slate-600 transition-colors hover:bg-slate-50 hover:text-slate-900"
							onclick={() => (caseStudiesDropdownOpen = false)}
						>
							{study.label}
						</a>
					{/each}
				</div>
				</div>
			{/if}
		</div>

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			class="relative"
			onmouseenter={() => (toolsDropdownOpen = true)}
			onmouseleave={() => (toolsDropdownOpen = false)}
		>
				<a
					href="/tools"
					class="inline-flex items-center gap-1 rounded-md px-3 py-2 text-sm font-medium transition-colors
						{isActive('/tools')
						? 'bg-slate-100 text-navy-700'
						: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
					aria-current={isActive('/tools') ? 'page' : undefined}
				>
					Tools
					<svg
						class="h-4 w-4 transition-transform {toolsDropdownOpen ? 'rotate-180' : ''}"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						stroke-width="2"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
					</svg>
				</a>
				{#if toolsDropdownOpen}
					<div class="absolute left-0 top-full z-50 w-64 pt-2">
					<div
						class="rounded-lg border border-slate-200 bg-white py-1 shadow-lg"
					>
						{#each toolLinks as tool}
							<a
								href={tool.href}
								class="block px-4 py-2.5 text-sm text-slate-600 transition-colors hover:bg-slate-50 hover:text-slate-900"
								onclick={() => (toolsDropdownOpen = false)}
							>
								{tool.label}
							</a>
						{/each}
					</div>
					</div>
				{/if}
			</div>

			<a
				href="/contact"
				class="ml-4 rounded-lg bg-navy-900 px-4 py-2 text-sm font-semibold text-white transition-colors hover:bg-navy-800"
			>
				Get in Touch
			</a>
		</div>

		<button
			class="inline-flex items-center justify-center rounded-md p-2 text-slate-600 transition-colors hover:bg-slate-100 hover:text-slate-900 md:hidden"
			onclick={() => (menuOpen = !menuOpen)}
			aria-expanded={menuOpen}
			aria-controls="mobile-menu"
			aria-label={menuOpen ? 'Close menu' : 'Open menu'}
		>
			{#if menuOpen}
				<svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
					<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
				</svg>
			{:else}
				<svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
					<path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
				</svg>
			{/if}
		</button>
	</nav>

	{#if menuOpen}
		<div id="mobile-menu" class="border-t border-slate-200 bg-white md:hidden">
			<div class="space-y-1 px-4 py-4">
				{#each links as link}
					<a
						href={link.href}
						onclick={() => (menuOpen = false)}
						class="block rounded-md px-3 py-2.5 text-base font-medium transition-colors
							{isActive(link.href)
							? 'bg-slate-100 text-navy-700'
							: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
						aria-current={isActive(link.href) ? 'page' : undefined}
					>
						{link.label}
					</a>
				{/each}

			<button
				onclick={() => (mobileAboutOpen = !mobileAboutOpen)}
				class="flex w-full items-center justify-between rounded-md px-3 py-2.5 text-base font-medium transition-colors
					{isActive('/about')
					? 'bg-slate-100 text-navy-700'
					: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
			>
				About
				<svg
					class="h-4 w-4 transition-transform {mobileAboutOpen ? 'rotate-180' : ''}"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
				>
					<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
				</svg>
			</button>
			{#if mobileAboutOpen}
				<div class="space-y-1 pl-4">
					<a
						href="/about"
						onclick={() => (menuOpen = false)}
						class="block rounded-md px-3 py-2 text-sm font-medium text-slate-500 transition-colors hover:bg-slate-50 hover:text-slate-900"
					>
						Company
					</a>
					{#each aboutLinks as link}
						{#if link.separator}
							<span class="mt-1 block px-3 pt-2 pb-0.5 text-[10px] font-semibold uppercase tracking-wider text-slate-400">{link.separator}</span>
						{/if}
						<a
							href={link.href}
							onclick={() => (menuOpen = false)}
							class="block rounded-md px-3 py-2 text-sm font-medium text-slate-500 transition-colors hover:bg-slate-50 hover:text-slate-900"
						>
							{link.label}
						</a>
					{/each}
				</div>
			{/if}

			<button
				onclick={() => (mobileCaseStudiesOpen = !mobileCaseStudiesOpen)}
				class="flex w-full items-center justify-between rounded-md px-3 py-2.5 text-base font-medium transition-colors
					{isActive('/case-studies')
					? 'bg-slate-100 text-navy-700'
					: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
			>
				Case Studies
				<svg
					class="h-4 w-4 transition-transform {mobileCaseStudiesOpen ? 'rotate-180' : ''}"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
				>
					<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
				</svg>
			</button>
			{#if mobileCaseStudiesOpen}
				<div class="space-y-1 pl-4">
					<a
						href="/case-studies"
						onclick={() => (menuOpen = false)}
						class="block rounded-md px-3 py-2 text-sm font-medium text-slate-500 transition-colors hover:bg-slate-50 hover:text-slate-900"
					>
						All Case Studies
					</a>
					{#each caseStudyLinks as study}
						<a
							href={study.href}
							onclick={() => (menuOpen = false)}
							class="block rounded-md px-3 py-2 text-sm font-medium text-slate-500 transition-colors hover:bg-slate-50 hover:text-slate-900"
						>
							{study.label}
						</a>
					{/each}
				</div>
			{/if}

			<button
				onclick={() => (mobileToolsOpen = !mobileToolsOpen)}
				class="flex w-full items-center justify-between rounded-md px-3 py-2.5 text-base font-medium transition-colors
					{isActive('/tools')
					? 'bg-slate-100 text-navy-700'
					: 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'}"
			>
				Tools
					<svg
						class="h-4 w-4 transition-transform {mobileToolsOpen ? 'rotate-180' : ''}"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						stroke-width="2"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
					</svg>
				</button>
				{#if mobileToolsOpen}
					<div class="space-y-1 pl-4">
						<a
							href="/tools"
							onclick={() => (menuOpen = false)}
							class="block rounded-md px-3 py-2 text-sm font-medium text-slate-500 transition-colors hover:bg-slate-50 hover:text-slate-900"
						>
							All Tools
						</a>
						{#each toolLinks as tool}
							<a
								href={tool.href}
								onclick={() => (menuOpen = false)}
								class="block rounded-md px-3 py-2 text-sm font-medium text-slate-500 transition-colors hover:bg-slate-50 hover:text-slate-900"
							>
								{tool.label}
							</a>
						{/each}
					</div>
				{/if}

				<a
					href="/contact"
					onclick={() => (menuOpen = false)}
					class="mt-2 block rounded-lg bg-navy-900 px-4 py-2.5 text-center text-base font-semibold text-white transition-colors hover:bg-navy-800"
				>
					Get in Touch
				</a>
			</div>
		</div>
	{/if}
</header>
