<script lang="ts">
	import { cn } from '$lib/helpers/style';
	import { ChevronRight } from 'lucide-svelte';
	import { getAccordionContext, getAccordionItemContext } from '.';
	import Button from '../button.svelte';

	const { trigger } = getAccordionContext();
	const item = getAccordionItemContext();

	let className: string | undefined | null = undefined;
	export { className as class };
</script>

<Button
	use={[trigger]}
	{...$trigger(item)}
	variant="ghost"
	class={cn('active:scale-100 w-full group aria-expanded:text-foreground', className)}
>
	<slot />
	<ChevronRight
		size=16
		class="h-4 w-4 ml-auto text-primary transition group-aria-expanded:rotate-90 group-aria-expanded:transform"
	/>
</Button>
