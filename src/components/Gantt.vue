<template>
    <div>
        <h1>Gantt Chart</h1>

        <div class="row mt-5">
            <div v-for="(process, index) in processes">
                <div class="text-white processBlock"
                      :style="'width: '+ calculateProcessTime(index)
                      + 'em; background-color: ' + getColor(process.name)">
                    {{ process.name }}
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

        watch:  {
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
				if (index === 0) {
					return this.processes[index].timeEnd
				}

				return this.processes[index].timeEnd - this.processes[index-1].timeEnd
			},

            getColor(processName) {
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
        font-size: 1.5em;
        outline-color: black;
        outline-style: solid;
        outline-width: 2px;
    }
</style>
