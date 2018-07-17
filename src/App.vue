<template>
	<div>
		<github-ribbon />
		<h1>Live demos for <a href="https://github.com/cameronhimself/vue-drag-drop/">VueDragDrop</a></h1>
		<p>The source code for these demos is <a href="https://github.com/cameronhimself/vue-drag-drop-demo/tree/master/src">here</a>.</p>
		<div class="section">
			<h3>Minimal example</h3>
			<minimal></minimal>
		</div>
		<div class="section">
			<h3>Custom drag-over styling</h3>
			<styling></styling>
		</div>
		<div class="section">
			<h3>Custom tags</h3>
			<p>The default is div for the root element for both Drags and Drops, but you can use any tag you like.</p>
			<tags></tags>
		</div>
		<div class="section">
			<h3>Nested drag elements</h3>
			<p>You have to stopPropagation on the child's dragstart event, otherwise the parent's transfer data takes precedence.</p>
			<nested></nested>
		</div>
		<div class="section">
			<h3>Custom drag image</h3>
			<p>The simplest way to set a custom drag image is to use the 'image' prop.</p>
			<drag-image></drag-image>
		</div>
		<div class="section">
			<h3>Custom drag image with HTML</h3>
			<p>You can also use custom HTML for the drag image using the 'image' slot. When using HTML for the drag image, the spec requires it to be visible, so the component will render it off-screen using 'position: fixed'. If you'd prefer it didn't do this for you, you can set the 'hide-image-html' prop to false.</p>
			<drag-html></drag-html>
		</div>
		<div class="section">
			<h3>Drop effects (cursors)</h3>
			<drop-effects></drop-effects>
		</div>
		<div class="section">
			<h3>Exclusive groups</h3>
			<p>No magic here. Control how your app behaves with simple props and data.</p>
			<groups></groups>
		</div>
		<div class="section">
			<h3>Basic list support</h3>
			<p>There are plenty of existing components that handle this much more robustly, mostly using sortable.js or dragula behind the scenes, but if you don't need all their bells and whistles this works in a basic way that's much more light-weight.</p>
			<lists></lists>
		</div>
		<div class="section">
			<h3>Files</h3>
			<p>Nothing special&mdash;use the native event's 'files' object.</p>
			<files></files>
		</div>
		<div class="section">
			<h3>Scoped slots</h3>
			<p>The drag transfer data is also provided via scope data in the default slot. It's arguably better to handle the transfer data using standard prop flow in your application, but using the scoped slot is quick and easy. It's also a simple way to check if a drag is in progress over a dropzone, which can be tricky to do: if the transfer-data is set on the Drop, you know a drag is in progress.</p>
			<scoped></scoped>
		</div>
	</div>
</template>

<script>
	import GithubRibbon from './GithubRibbon.vue';
	import Minimal from './Minimal.vue';
	import Tags from './Tags.vue';
	import Styling from './Styling.vue';
	import Nested from './Nested.vue';
	import DragImage from './DragImage.vue';
	import DragHtml from './DragHtml.vue';
	import DropEffects from './DropEffects.vue';
	import Groups from './Groups.vue';
	import Lists from './Lists.vue';
	import Files from './Files.vue';
	import Scoped from './Scoped.vue';

	export default {
		components: { GithubRibbon, Minimal, Tags, Styling, Nested, DragImage, DragHtml, DropEffects, Groups, Lists, Files, Scoped },
	};
</script>

<style>
	html {
		font-family: 'Arial', sans-serif;
	}

	body {
		padding: 40px 90px;
		line-height: 1.5;
	}

	.section {
		margin-top: 30px;
		margin-bottom: 50px;
	}

	.drag, .drop {
		box-sizing: border-box;
		display: inline-block;
		border-radius: 10px;
		width: 100px;
		height: 100px;
		background: #ccc;
		vertical-align: middle;
		margin-right: 20px;
		position: relative;
		padding: 5px;
		padding-top: 35px;
		text-align: center;
		margin: 3px;
	}

	.drag {
		color: #fff;
		cursor: move;
		background: #777;
		border-right: 2px solid #666;
		border-bottom: 2px solid #666;
	}

	.drop {
		background: #eee;
		border-top: 2px solid #ccc;
		border-left: 2px solid #ddd;
	}
</style>
