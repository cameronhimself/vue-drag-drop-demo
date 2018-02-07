<template>
	<div>
		<drag class="drag"
			:image="require('./assets/drag.png')"
			:transfer-data="{ example: 'drag-image' }">
			drag
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
