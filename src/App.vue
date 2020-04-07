<template>
  <div id="app" class="container">
    <h1>Create Gantt Charts for CPU Processes</h1>

    <div class="row">
      <processes :processes="processes" class="mx-auto" />
    </div>
  </div>
</template>

<script>
  import processes from "@/components/Processes"
export default {
  name: 'App',
  components: { processes },

  data() {
    return {
      processes: [
        {
          id: 0,
          name: 'P1',
          timeEnd: 10
        },
        {
          id: 1,
          name: 'P2',
          timeEnd: 20
        },
        {
          id: 2,
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
