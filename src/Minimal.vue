<template>
	<div>
		<drag :transfer-data="{ example: 'minimal' }">drag</drag>
		<drop @drop="handleDrop">drop</drop>
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
