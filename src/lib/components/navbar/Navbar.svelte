<script lang="ts">
	import { onDestroy, onMount } from 'svelte';
	import { Button } from '$lib/components/ui/button';
	import {
		NavigationMenuRoot,
		NavigationMenuItem,
		NavigationMenuLink,
		NavigationMenuList,
	} from '$lib/components/ui/navigation-menu';

	const navLinks = ['Systems', 'Studios', 'Signals', 'Contact'];

	let hidden = false;
	let solid = false;
	let lastY = 0;

	function handleScroll() {
		if (typeof window === 'undefined') return;
		const y = window.scrollY;
		const delta = y - lastY;

		if (Math.abs(delta) > 4) {
			hidden = delta > 0 && y > 40;
		}

		solid = y > 12;
		lastY = y;
	}

	onMount(() => {
		if (typeof window !== 'undefined') {
			lastY = window.scrollY;
			window.addEventListener('scroll', handleScroll, { passive: true });
		}
	});

	onDestroy(() => {
		if (typeof window !== 'undefined') {
			window.removeEventListener('scroll', handleScroll);
		}
	});
</script>

<nav
	class={`fixed inset-x-0 top-0 z-40 flex justify-center transition-transform duration-200 ${hidden ? '-translate-y-full' : 'translate-y-0'}`}
>
	<div
		class={`mt-3 w-full max-w-6xl px-4 sm:px-6 lg:px-8 rounded-2xl border border-border/40 backdrop-blur-2xl transition-all duration-200 ${solid ? 'bg-background/70 shadow-lg ring-1 ring-white/30' : 'bg-background/40 shadow-md ring-1 ring-white/20'}`}
	>
		<div class="flex items-center justify-between gap-4 py-3">
			<div class="flex items-center gap-2 text-foreground">
				<p class="text-sm font-semibold tracking-tight">MCP</p>
				<span class="text-sm text-muted-foreground">Studio network</span>
			</div>

			<NavigationMenuRoot class="hidden flex-1 justify-center md:flex">
				<NavigationMenuList class="flex gap-6 text-sm text-muted-foreground">
					{#each navLinks as link}
						<NavigationMenuItem>
							<NavigationMenuLink
								href="#"
								class="transition-colors hover:text-foreground"
							>
								{link}
							</NavigationMenuLink>
						</NavigationMenuItem>
					{/each}
				</NavigationMenuList>
			</NavigationMenuRoot>

			<Button variant="outline" size="sm" class="rounded-full">
				Access
			</Button>
		</div>
	</div>
</nav>
