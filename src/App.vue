<template>
	<div id="app" class="container-fluid">
		<h1>Create Gantt Charts for CPU Processes</h1>

		<div class="row mt-5">
			<processes :processes="processes" class="mx-auto"/>
		</div>

		<div class="row mt-5">
			<gantt :processes="processes" class="mx-auto"/>
		</div>

		<div class="row mt-5 mb-5">
			<div class="mx-auto">
				Created by <strong>Yiannis Kiranis</strong> (2020)
				<br><a href="https://apps4net.eu">apps4net.eu</a> |
				<a href="https://github.com/ikiranis/gantt">Source code</a>
			</div>
		</div>

	</div>
</template>

<script>
	import processes from "@/components/Processes"
	import gantt from "@/components/Gantt"

	export default {
		name: 'App',
		components: {processes, gantt},

		data() {
			return {
				processes: [
					{
						name: 'P1',
						timeEnd: 10
					},
					{
						name: 'P2',
						timeEnd: 20
					},
					{
						name: 'P3',
						timeEnd: 30
					}
				]
			}
		}
	}
</script>

<style>

	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
