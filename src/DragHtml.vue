<template>
	<div>
		<drag class="drag" :transferData="{ example: 'drag-html' }">
			drag
			<div slot="image" class="drag-image">
				<ul>
					<li>Drag</li>
					<li>Image</li>
					<li>HTML</li>
				</ul>
			</div>
		</drag>
		<drop class="drop" @drop="handleDrop">drop</drop>
	</div>
</template>

<script>
	import { Drag, Drop } from 'vue-drag-drop';

	export default {
		components: { Drag, Drop },
		methods: {
			handleDrop(data) {
				alert(`You dropped with data: ${JSON.stringify(data)}`);
			},
		},
	};
</script>

<style>
	.drag-image {
		color: #000;
	}
</style>
