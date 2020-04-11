<template>
    <div class="container col-lg-6">
        <div v-for="(process, index) in processes">
            <div class="form-group row">
                <div class="col-lg-6">
                    <input id="name" type="text" class="form-control"
                           v-model="process.name"
                           placeholder="Process Name" required maxlength="3">
                </div>
                <div class="col-lg-4">
                    <input id="timeEnd" type="number" class="form-control"
                           v-model="process.timeEnd"
                           placeholder="Time End" required min="1" max="99">
                </div>

                <button class="btn btn-danger col" @click="removeProcess(index)">Remove</button>
            </div>
        </div>

        <button class="btn btn-success col-12 col-lg-6" name="add" @click="addProcess">Add process</button>
    </div>
</template>

<script>
	export default {
		data() {
			return {}
		},

		props: {
			processes: {
				required: true,
				type: Array
			}
		},

		methods: {
			addProcess() {
				let lastProcess = this.processes[this.processes.length - 1]

				this.processes.push({
					name: '',
					timeEnd: parseInt(lastProcess.timeEnd) + 1
				})
			},

			removeProcess(index) {
				this.processes.splice(index, 1)
			}
		}
	}
</script>
