<script>
	import { twMerge } from 'tailwind-merge';

	/**
	 * @type {File}
	 */
	export let item;

	$: name = item.name.replace(/[_-]/g, ' ').replace(/\.mp4/g, '');
	$: size = (item.size / 1000000).toFixed(1) + ' mb';

	$: classList = twMerge('flex items-center space-x-2 w-full text-left', $$props.class);
</script>

<button class={classList} on:click>
	<img src="https://picsum.photos/50/50" alt="Video thumbnail" class="w-12 h-12 rounded-lg" />
	<div class="grow overflow-hidden">
		<h3 class="text-lg font-medium whitespace-nowrap text-ellipsis overflow-hidden">
			{name}
		</h3>
		<p class="text-gray-500">{size}</p>
	</div>
</button>
