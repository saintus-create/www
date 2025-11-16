<script lang="ts">
	import { Moon, Sun } from '@lucide/svelte'
	import { resetMode, setMode } from 'mode-watcher'
	import { buttonVariants } from '$lib/components/ui/button'
	import { cn } from '$lib/utils'
	import {
		DropdownMenu,
		DropdownMenuContent,
		DropdownMenuItem,
		DropdownMenuTrigger,
	} from '$lib/components/ui/dropdown-menu'

	const options = [
		{ label: 'Light', action: () => setMode('light') },
		{ label: 'Dark', action: () => setMode('dark') },
		{ label: 'System', action: () => resetMode() },
	]
</script>

<DropdownMenu>
	<DropdownMenuTrigger
		class={cn(buttonVariants({ variant: 'outline', size: 'icon' }), 'relative')}
	>
		<Sun class="h-4 w-4 rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0" />
		<Moon class="absolute h-4 w-4 rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100" />
		<span class="sr-only">Toggle theme</span>
	</DropdownMenuTrigger>
	<DropdownMenuContent align="end" class="w-40">
		{#each options as option}
			<DropdownMenuItem
				on:select={(event) => {
					event.preventDefault()
					option.action()
				}}
			>
				{option.label}
			</DropdownMenuItem>
		{/each}
	</DropdownMenuContent>
</DropdownMenu>
