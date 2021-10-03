<template>
<div class="container">
<Header    @toggleAddTask="this.showAddTask = !this.showAddTask" title="shubham" />
<AddTask v-if="showAddTask" @add-todo="addTodo"/>
<Tasks  @mark-completed="markdone" :tasks="tasks"   @deleted="deletetask"/>
  <h3 v-if="this.tasks.length ==0">You do not have any tasks!</h3>

</div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from  './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return {
      tasks : [],
        showAddTask: false

    }
  },
  methods:{
    markdone(id){
        this.tasks.map(item=> {
          if(item.id===id){
            item.completed = !item.completed
          }
        })
        let todoArray = JSON.parse(localStorage.getItem('tasks'));
        todoArray.map(item=> {
           if(item.id===id){
            item.completed = !item.completed
          }
        })
        localStorage.setItem('tasks' , JSON.stringify(todoArray))
       
    },
    deletetask(id){
      // console.log('deleted')
      if(confirm('Are you sure?')){
       this.tasks = this.tasks.filter(item=> item.id!=id)
       let todoArray = JSON.parse(localStorage.getItem('tasks'));
      todoArray=  todoArray.filter(item=> item.id!= id);
      localStorage.setItem('tasks' , JSON.stringify(todoArray))


      }
       
    },
    addTodo(todo){
      this.tasks.push(todo);
      let todoArray = JSON.parse(localStorage.getItem('tasks'));
      todoArray.push(todo);
      localStorage.setItem('tasks' , JSON.stringify(todoArray))
    }
  },
  created(){
     if(localStorage.getItem('tasks') === null){
      localStorage.setItem('tasks', JSON.stringify(this.tasks))
    }else{
      this.tasks = JSON.parse(localStorage.getItem('tasks'))
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;500&display=swap');
.container{
   /* height: 400px; */
     width: 400px;
     margin:  100px auto;
     padding-bottom: 20px;
    
     box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
     background-color: white;
     border-radius: 5px;
     
}
*{
  box-sizing: border-box;
}
body{
     font-family: 'Roboto', sans-serif;
    background-color: #F3F0D7;
}
h3{
  text-align: center;
}
</style>
