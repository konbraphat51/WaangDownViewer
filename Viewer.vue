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
.MarkDownViwer {
	font-family: Arial, Helvetica, sans-serif;
}

.MarkDownViwer p {
	margin: 0 0.5rem 0.5rem 0.7rem;
}

.MarkDownViwer h1 {
	font-size: 4em;
	padding: 0.1em 0;
	border-top: solid 3px #81d498;
	border-bottom: solid 3px #81d498;
	text-align: center;
	margin: 0 auto 1.5rem;
}

.MarkDownViwer h2 {
	font-size: 1.5rem;
	padding: 0.2em 0.3rem;
	color: #000000;
	background: #e1ffd9;
	border-left: solid 5px #589e67;
	margin : 0 0 0.5em;
  }

.MarkDownViwer h3 {
	font-size: 1.5rem;
	padding : 0 0.2rem;
	border-bottom: solid 2px #81d498;
	width: 60%;
	margin: 0 0 0.5em;
}

.MarkDownViwer h4 {
	font-size: 1.5rem;
	padding : 0 0.2rem;
	margin : 0 0 0.5em;
}

.MarkDownViwer h5 {
	font-size: 1.2rem;
	padding : 0 0.4rem;
	margin : 0 0 0.5em;
}

.MarkDownViwer h6 {
	font-size: 1rem;
	padding : 0 0.8rem;
	margin : 0 0 0.5em;
}

</style>