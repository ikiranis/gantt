<template>
	<div class="px-5">
		<h1>Gantt Chart</h1>

		<div class="row mt-5">
			<div v-for="(process, index) in processes">
				<div class="text-white processBlock"
					 :style="'width: '+ calculateProcessTime(index)
                      + 'em; background-color: ' + getProcessColor(process.name)">
					<span>{{ (process.name) !== '' ? process.name : '?' }}</span>
				</div>

				<div class="row mt-1">
					<div v-if="index === 0" class="mr-auto ml-3">0</div>
					<div class="ml-auto mr-3">{{ process.timeEnd }}</div>
				</div>
			</div>
		</div>
	</div>

</template>

<script>
	export default {
		data() {
			return {
				processColors: [],

				colors: [
					'green',
					'blueviolet',
					'burlywood',
					'darkgreen',
					'crimson',
					'darkolivegreen',
					'indigo',
					'darkslateblue',
					'mediumorchid',
					'goldenrod',
					'orangered'
				]
			}
		},

		props: {
			processes: {
				required: true,
				type: Array
			}
		},

		computed: {
			//
		},

		watch: {
			processes: {
				deep: true,

				handler() {
					this.getProcessColors()
				}
			}
		},

		created() {
			this.getProcessColors()
		},

		methods: {
			getProcessColors() {
				let uniqueProcesses = []
				let color = 0

				this.processes.forEach(item => {
					if (!uniqueProcesses.includes(item.name)) {
						uniqueProcesses.push({
							name: item.name,
							color: this.colors[color]
						})

						color = (color === 10) ? 0 : color + 1
					}
				})

				this.processColors = uniqueProcesses
			},

			calculateProcessTime(index) {
				let lastProcess = this.processes[this.processes.length - 1]
				let ratio = 1

				if (lastProcess.timeEnd > 40) {
					ratio = parseInt(lastProcess.timeEnd / 40) + 1
				}

				if (index === 0) {
					return (this.processes[index].timeEnd * 2) / ratio
				}

				return ((this.processes[index].timeEnd - this.processes[index - 1].timeEnd) * 2) / ratio
			},

			getProcessColor(processName) {
				let found = this.processColors.find(item => {
					return item.name === processName
				})

				return found.color
			}
		}
	}
</script>

<style scoped>
	.processBlock {
		display: block;
		font-size: 1.3em;
		outline-color: black;
		outline-style: solid;
		outline-width: 2px;
	}
</style>
