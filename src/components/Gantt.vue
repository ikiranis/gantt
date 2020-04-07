<template>
    <div>
        <h1>Gantt Chart</h1>

        <div class="row mt-5">
            <span v-for="process in processes" class="col">
                {{ process.name }}
            </span>
        </div>
    </div>

</template>

<script>
	export default {
		data() {
			return {
                uniqueProcesses: []
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
			processes() {
				let uniqueProcesses = []

				this.processes.forEach(item => {
					if (!uniqueProcesses.includes(item.name)) {
						uniqueProcesses.push(item.name)
					}
				})

				this.uniqueProcesses = uniqueProcesses
            }
        },

		methods: {
            //
		}
	}
</script>
