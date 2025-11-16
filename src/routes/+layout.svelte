<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import Navbar from '$lib/components/navbar/Navbar.svelte';
	import { ModeWatcher } from 'mode-watcher';
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="relative min-h-screen bg-background text-foreground">
	<ModeWatcher />
	<Navbar />
	<div class="pointer-events-none absolute inset-0 z-0 overflow-hidden" aria-hidden="true">
		<div class="absolute inset-0 bg-gradient-to-b from-white/35 via-transparent to-transparent mix-blend-screen opacity-75 dark:from-transparent"></div>
		<div class="absolute inset-0 bg-[radial-gradient(circle_at_15%_20%,rgba(255,255,255,0.25),transparent_55%),radial-gradient(circle_at_80%_0%,rgba(255,255,255,0.18),transparent_45%),radial-gradient(circle_at_50%_0%,rgba(255,255,255,0.12),transparent_60%)] blur-3xl opacity-70 dark:opacity-20 dark:mix-blend-overlay"></div>
	</div>
	<main
		class="relative z-10 pt-20 md:pt-24 pb-16 px-4 sm:px-6 lg:px-10 w-full max-w-6xl mx-auto grid grid-cols-12 gap-x-4 gap-y-12"
	>
		<slot />
	</main>
</div>
