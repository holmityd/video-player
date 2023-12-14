<script>
	import FileInput from './../lib/FileInput.svelte';
	import ListItem from './../lib/ListItem.svelte';
	import { Player } from 'playeronix';
	import { filesStore } from '../lib/player.store';
	import { onMount } from 'svelte';

	/**
	 * @type {File?}
	 */
	let active;
	/**
	 * @param {File} item
	 */
	function changeActive(item) {
		active = item;
	}
	$: activeSrc = active ? URL.createObjectURL(active) : undefined;

	onMount(() => {});
</script>

<div class="flex h-screen">
	<FileInput />

	{#if $filesStore}
		<div class="w-3/4">
			<!-- Video Player -->
			<Player src={activeSrc} style="youtube" />
		</div>
		<div class="w-1/4 p-4">
			<!-- Video List -->
			<ul class="space-y-4">
				{#each $filesStore as item}
					<li class={active === item ? 'bg-cyan-600' : ''}>
						<ListItem {item} on:click={() => changeActive(item)} />
					</li>
				{/each}
				<!-- Repeat video list items -->
			</ul>
		</div>
	{/if}
</div>
