<script>
	import { filesStore } from '../lib/player.store';
	// @ts-ignore
	function previewVideos({ target }) {
		filesStore.set(Array.from(target.files));
	}
</script>

<label for="file">
	<input id="file" type="file" accept="video/mp4" multiple on:change={previewVideos} />
</label>
