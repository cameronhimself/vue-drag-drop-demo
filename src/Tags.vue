<template>
	<div>
		<drag class="drag" :tag="'span'" :transfer-data="{ example: 'tags' }">drag</drag>
		<drop class="drop"
			:class="{ over }"
			:tag="'span'"
			@dragover="over = true"
			@dragleave="over = false"
			@drop="handleDrop">
				drop
		</drop>
	</div>
</template>

<script>
	import { Drag, Drop } from 'vue-drag-drop';

	export default {
		components: { Drag, Drop },
		data: function () {
			return { over: false };
		},
		methods: {
			handleDrop(data) {
				this.over = false;
				alert(`You dropped with data: ${JSON.stringify(data)}`);
			},
		},
	};
</script>

<style>
	.drop.over {
		border-color: #aaa;
		background: #ccc;
	}
</style>
