<template>
	<div>
		<div>
			<drag v-for="group in groups" class="drag"
				:key="group"
				:transfer-data="{ group, example: 'groups' }"
				@dragstart="dragging = group"
				@dragend="dragging = null">
					{{ group }}
			</drag>
		</div>
		<div>
			<drop v-for="group in groups" class="drop"
				:key="group"
				:class="{ allowed: dragging === group }"
				@dragover="handleDragover(group, ...arguments)"
				@drop="handleDrop">
					{{ group }}
			</drop>
		</div>
	</div>
</template>

<script>
	import { Drag, Drop } from 'vue-drag-drop';

	export default {
		components: { Drag, Drop },
		data: function () {
			return {
				groups: ['A', 'B', 'C'],
				dragging: null,
			};
		},
		methods: {
			handleDragover(group, data, event) {
				if (group !== data.group) {
					event.dataTransfer.dropEffect = 'none';
				}
			},
			handleDrop(data) {
				alert(`You dropped with data: ${JSON.stringify(data)}`);
			},
		},
	};
</script>

<style>
	.drag, .drop {
		display: inline-block;
	}
	.drop.allowed {
		background-color: #dfd;
	}
</style>
