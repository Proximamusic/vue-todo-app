<template>
  <div class="add-task">
      <label for="">Task</label>
    <input v-model="taskText" type="text" placeholder="task" />
      <label for="">Deadline</label>

    <input v-model="taskDeadline" type="text" placeholder="deadline" />
    <button @click="addTodo(this.taskText, this.taskDeadline)"  :disabled="this.taskText.length==0">ADD</button>
  </div>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      taskText: '',
      taskDeadline: ''
    }
  },
  methods:{
      addTodo(taskText, taskDeadline){
          this.$emit('add-todo', {
              id: Math.floor(Math.random() * 10000),
              text: taskText,
              completed: false,
              deadline: taskDeadline,
          })
          this.taskText = '';
          this.taskDeadline= ''
      }
  }
};
</script>


<style scoped>
.add-task {
  display: flex;
  flex-direction: column;
  width: 90%;
  margin: auto;
  /* align-items: center; */

}
label{
  align-self: flex-start;

}
input {
  margin-bottom: 10px;
  height: 30px;
  outline: none;
  border: 1px solid grey;
  color: black;
  border-radius: 3px;
  padding-left: 5px;

}
button {
  width: 100%;
  padding: 5px 0;
  border-radius: 2px;
  border: none;
  background-color: rgb(148, 148, 148);
  color: white;
}
</style>