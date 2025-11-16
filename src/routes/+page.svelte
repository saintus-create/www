<script lang="ts">
	import ThemeToggle from '$lib/components/theme-toggle.svelte';
	import { Button } from '$lib/components/ui/button';
	import {
		Card,
		CardContent,
		CardDescription,
		CardHeader,
		CardTitle,
	} from '$lib/components/ui/card';

	const featureSections = [
		{
			tag: 'Unlock the web',
			title: 'Bring ChatGPT anywhere you browse',
			copy: 'Atlas stays anchored to the page you are on, so it can summarize source material, fill forms, and capture details without tab juggling.',
			cta: 'See browser view',
			preview: 'Browser context',
		},
		{
			tag: 'Pick up where you left off',
			title: 'Sessions remember the work in progress',
			copy: 'When you reopen a tab, Atlas restores the conversation and the actions it took, letting you continue drafting or reviewing instantly.',
			cta: 'Review history',
			preview: 'Timeline resumes',
		},
		{
			tag: 'Take action for you',
			title: 'Atlas can execute steps with a single request',
			copy: 'From capturing research to booking follow-ups, Atlas runs the clicks for you while keeping every action visible and undoable.',
			cta: 'Watch it act',
			preview: 'Automations',
		},
		{
			tag: 'Assist anywhere',
			title: 'Surface Atlas exactly when you need it',
			copy: 'Highlight text, open the command palette, or tap the tray icon. Atlas meets you at the cursor without covering your work.',
			cta: 'Open palette',
			preview: 'Inline helper',
		},
	];

	const infoTiles = [
		{
			title: 'You are in control',
			copy: 'Visibility toggles keep Atlas private until you invite it into a page, and you can pause access anytime.',
		},
		{
			title: 'Assistants you trust',
			copy: 'Atlas references sources directly from the tab so you can inspect anything it summarizes or drafts.',
		},
		{
			title: 'Simple to share',
			copy: 'Hand off sessions to teammates with a link, or export insights into the systems you already use.',
		},
	];

	let scrollY = 0;

	const handleScroll = (event: Event) => {
		const target = event.currentTarget as Window;
		scrollY = target.scrollY;
	};

	const clamp = (value: number, min: number, max: number) => Math.min(Math.max(value, min), max);

	const getParallaxStyle = (offset = 0, strength = 0.04, limit = 36) => {
		const shift = clamp((scrollY - offset) * strength, -limit, limit);
		const opacity = 1 - Math.min(Math.abs(shift) / (limit * 2), 0.25);
		return `transform: translateY(${-shift}px); opacity: ${opacity.toFixed(3)}`;
	};
</script>

<svelte:window on:scroll={handleScroll} />

<section class="col-span-12">
	<Card
		class="relative overflow-hidden border-none bg-gradient-to-b from-primary/40 via-primary/5 to-background px-6 py-16 text-center shadow-none"
		style={getParallaxStyle(0, 0.05, 30)}
	>
		<div class="absolute right-6 top-6">
			<ThemeToggle />
		</div>
		<CardContent class="mx-auto flex max-w-4xl flex-col items-center gap-10 p-0">
			<div class="inline-flex items-center gap-2 rounded-full bg-primary/20 px-4 py-1 text-xs font-semibold text-white">
				New
				<span class="text-white/80">Atlas preview</span>
			</div>
			<div class="space-y-4">
				<h1 class="text-4xl font-semibold tracking-tight text-foreground sm:text-5xl">ChatGPT Atlas</h1>
				<p class="text-base text-muted-foreground sm:text-lg">
					Meet ChatGPT where work already happens. Atlas is a lightweight companion that fades into the page while staying ready to finish the task.
				</p>
			</div>
			<div class="flex flex-col gap-3 sm:flex-row">
				<Button size="lg">Get started</Button>
				<Button variant="ghost" size="lg">Watch demo</Button>
			</div>
			<Card class="w-full max-w-xl border border-border/50 bg-card shadow-lg">
				<CardContent class="space-y-4 px-8 py-10">
					<p class="text-sm font-medium text-muted-foreground">Meet Atlas</p>
					<p class="text-2xl font-semibold text-foreground">ChatGPT rides along</p>
					<p class="text-sm text-muted-foreground">
						Stay in flow with a companion that notices context and suggests the next move without filling the screen.
					</p>
				</CardContent>
			</Card>
		</CardContent>
	</Card>
</section>

{#each featureSections as feature, index}
	<Card class="col-span-12 overflow-hidden" style={getParallaxStyle(300 + index * 420, 0.04, 26)}>
		<CardContent class={`flex flex-col gap-10 p-6 md:p-10 ${index % 2 ? 'md:flex-row-reverse' : 'md:flex-row'}`}>
			<div class="md:w-1/2 space-y-4">
				<p class="text-xs font-semibold uppercase tracking-wide text-muted-foreground">{feature.tag}</p>
				<CardTitle class="text-3xl font-semibold tracking-tight">{feature.title}</CardTitle>
				<CardDescription class="text-base leading-relaxed text-muted-foreground">{feature.copy}</CardDescription>
				<Button variant="link" class="px-0 text-base text-primary">{feature.cta}</Button>
			</div>
			<div class="md:w-1/2">
				<div
					class="relative aspect-[4/3] w-full rounded-3xl border border-border bg-muted/30"
					style={getParallaxStyle(400 + index * 420, 0.03, 18)}
				>
					<div class="absolute inset-0 flex flex-col items-center justify-center gap-2 text-center text-muted-foreground">
						<span class="text-sm font-semibold">{feature.preview}</span>
						<span class="text-xs text-muted-foreground/80">Interactive preview</span>
					</div>
				</div>
			</div>
		</CardContent>
	</Card>
{/each}

<section class="col-span-12 grid gap-4 md:grid-cols-3">
	{#each infoTiles as tile}
		<Card class="bg-muted/20">
			<CardHeader>
				<CardTitle class="text-lg">{tile.title}</CardTitle>
				<CardDescription class="text-sm leading-relaxed">{tile.copy}</CardDescription>
			</CardHeader>
		</Card>
	{/each}
</section>

<Card class="col-span-12 overflow-hidden border-none bg-gradient-to-b from-primary/10 via-background to-background text-center">
	<CardContent class="space-y-6 px-6 py-16">
		<div class="mx-auto inline-flex items-center justify-center gap-2 rounded-full bg-primary/20 px-4 py-1 text-xs font-semibold text-white">
			Download
			<span class="text-white/80">Atlas preview</span>
		</div>
		<CardTitle class="text-3xl tracking-tight">Bring ChatGPT Atlas anywhere</CardTitle>
		<CardDescription class="mx-auto max-w-2xl text-base text-muted-foreground">
			Install the companion, sign in with your ChatGPT account, and keep the assistant ready on every page you open.
		</CardDescription>
		<div class="flex flex-col items-center justify-center gap-3 sm:flex-row">
			<Button size="lg">Download for desktop</Button>
			<Button variant="ghost" size="lg">Use at work</Button>
		</div>
	</CardContent>
</Card>
