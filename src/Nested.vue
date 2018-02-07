<template>
	<div>
		<drag class="drag" :transferData="{ example: 'nested', position: 'parent' }">
			parent
			<drag class="drag" @dragstart="handleChildDragstart" :transferData="{ position: 'child' }">child</drag>
		</drag>
		<drop class="drop"
			:class="{ over }"
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
			handleChildDragstart(data, event) {
				event.stopPropagation();
			},
			handleDrop(data) {
				this.over = false;
				alert(`You dropped with data: ${JSON.stringify(data)}`);
			},
		},
	};
</script>

<style lang="scss" scoped>
	.drop.over {
		border-color: #aaa;
		background: #ccc;
	}
	.drag {
		padding-top: 10px;
		> .drag {
			padding: 10px;
			background: rgba(0,0,0,0.3);
			width: auto;
			height: auto;
		}
	}
</style>
