<template>
	<div>
		<drop class="drop" @drop="handleDrop">drop files</drop>
	</div>
</template>

<script>
	import { Drag, Drop } from 'vue-drag-drop';

	export default {
		components: { Drag, Drop },
		methods: {
			handleDrop(data, event) {
				event.preventDefault();
				const files = event.dataTransfer.files;
				const filenames = [];
				for (let i = 0; i < files.length; i++) {
					filenames.push(files.item(i).name);
				}
				alert(`You dropped files: ${JSON.stringify(filenames)}`);
			},
		},
	};
</script>
