<template>
	<div>
		<drag class="drag" :transfer-data="scopedData">
			<template scope="props">
				<div v-if="props.transferData">
					{{ props.transferData.dragText }}
				</div>
				<div v-else>drag me</div>
			</template>
		</drag>
		<drop class="drop" @drop="handleDrop">
			<template scope="props">
				<div class="drag" v-if="props.transferData">
					{{ props.transferData.dropText }}
				</div>
			</template>
		</drop>
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
		computed: {
			scopedData: () => ({
				dragText: 'scoped drag',
				dropText: 'scoped drop',
			}),
		},
	};
</script>

<style lang="scss" scoped>
	.drop {
		padding: 3px;
		.drag {
			opacity: 0.5;
			display: block;
			width: 100%;
			height: 100%;
			margin: 0;
		}
	}
</style>
