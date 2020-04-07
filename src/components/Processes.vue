<template>
    <div>
        <div v-for="process in processes">
            <div class="form-group row">
                <div class="col-lg-8">
                    <input id="name" type="text" class="form-control"
                           v-model="process.name"
                           placeholder="Process Name" required maxlength="20">
                </div>
                <div class="col-lg-4">
                    <input id="timeEnd" type="number" class="form-control"
                           v-model="process.timeEnd"
                           placeholder="Time End" required min="1" max="99">
                </div>
            </div>
        </div>

        <button class="btn btn-info" name="add" @click="addProcess">Add process</button>
    </div>
</template>

<script>
    export default {
    	data() {
    		return {

            }
        },

    	props: {
    		processes: {
				required: true,
				type: Array
            }
        },

        methods: {
    		addProcess()
            {
            	let newData = {
					name: '',
					timeEnd: null
				}

				this.$set(this.processes, this.processes.length, newData)

				// this.processes.push(newData)

            }
        }
    }
</script>
