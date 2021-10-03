<template>

  <div :class="task.completed?'task done' : 'task'" >
     <h3>{{task.text}}  <i @click="deleted(task.id)" class="fas fa-times"></i></h3>
     <p>{{task.deadline}}</p>
     <button @click="completed(task.id)"  class="btn-done">Done</button>

    
  </div>

</template>

<script>

export default ({
    name: 'Task',
    data(){
   return {
       isClicked: false
   }
    },
    props:{
       task:Object
    },
    methods:{
        completed(id){
            // this.isClicked= !this.isClicked;
            this.$emit('mark-completed', id);

        },
          deleted(id){
            this.$emit('deleted', id);

        }
    }

})
</script>

<style scoped>
.task{
      width: 90%;
      background-color: rgb(238, 236, 236);
      margin: auto;
      border-radius: 5px;
      box-shadow: 0 0 5px rgba(58, 41, 41, 0.3);
      padding: 0 0 0 10px;
      
      
  }
  h3{
      display: flex;
      justify-content: space-between;
      padding: 0 5px 0 0;
      cursor: pointer;
      align-items: center;
      font-weight: 400;
  }
  p{
      margin-top: -20px;
      font-weight: 300;
  }
  .fas{
      color: red;
  }
  .done{
      outline: 2px solid rgb(117, 117, 250);
      color: rgb(155, 155, 155);
      text-decoration: line-through;
  }
  .btn-done{
      background-color: rgb(77, 75, 75);
      color: white;
      border: none;
      margin-bottom: 3px;
      border-radius: 2px;
      cursor: pointer;
      /* margin-top: -50px; */

  }
</style>