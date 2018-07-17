<template>
	<div>
		<div>
			<drag class="drag"
				:transfer-data="{ example: 'drop effects (copy)' }"
				:effect-allowed="['copy']"
				drop-effect="copy"
			>"copy"</drag>
			<drag class="drag"
				:transfer-data="{ example: 'drop effects (move)' }"
				:effect-allowed="['move']"
				drop-effect="move"
			>"move"</drag>
			<drag class="drag"
				:transfer-data="{ example: 'drop effects (link)' }"
				:effect-allowed="['link']"
				drop-effect="link"
			>"link"</drag>
			<drag class="drag"
				:transfer-data="{ example: 'drop effects (none)' }"
				:effect-allowed="['none']"
				drop-effect="none"
			>"none"</drag>
		</div>
		<div>
			<drop class="drop"
				:class="{ over }"
				@dragover="over = true"
				@dragleave="over = false"
				@drop="handleDrop">
					drop
			</drop>
		</div>
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
