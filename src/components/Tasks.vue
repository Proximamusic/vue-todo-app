<template>
    <div :key="task.id" v-for="task in tasks">
       <Task @mark-completed="$emit('mark-completed', task.id)" :task="task"   @deleted="$emit('deleted', task.id)"  />
    </div>
</template>


<script>

import Task from './Task.vue'
export default ({
  name: "Tasks",
  props: {
      tasks: Array
  },
  components:{
      Task
  },
  emits:['mark-completed', 'deleted']

})
</script>


<style scoped>
  


</style>