<!-- Required:

<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>

-->
<template>
	<div class="MarkDownViwer">
		<div ref="markdown"></div>
	</div>
</template>

<script>
export default {
	name: "Viewer",
	props: {
		markdown: {
			type: String,
			required: true,
		},
	},
	mounted() {
		this.RenderMarkdown(this.markdown)
	},
	methods: {
		RenderMarkdown(newVal) {
			//skip if not rendered yet
			if (!this.$refs.markdown) return

			this.$refs.markdown.innerHTML = marked.parse(newVal)
		},
	},
	watch: {
		markdown: {
			immediate: true,
			handler(newVal) {
				this.RenderMarkdown(newVal)
			},
		},
	},
}
</script>

<style>
/* Styles removed - using markdown-pdf.css from MyMarkdownCSS repository */
</style>
