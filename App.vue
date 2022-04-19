<template>
	<div id="app" ref="document">
		<img width=200 src="./assets/logo.png">
		<router-view></router-view>
		<button @click="exportToPDF">Export to PDF</button>
	</div>
</template>

<script>
	import html2pdf from 'html2pdf.js'
	
	export default {
    name: 'app',
		methods: {
			exportToPDF () {
				html2pdf(this.$refs.document, {
					margin: 1,
					filename: 'document.pdf',
					image: { type: 'jpeg', quality: 0.98 },
					html2canvas: { dpi: 192, letterRendering: true },
					jsPDF: { unit: 'in', format: 'letter', orientation: 'landscape' }
				})
			}
		}
  }
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>