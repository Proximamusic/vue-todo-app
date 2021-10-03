<template>
    <header>
        <h1>task Keeper</h1>
        <Button  @toggleAddTask="$emit('toggleAddTask')" text="Add Item" color="rgb(141, 141, 247)"/>
    </header>
</template>

<script>
import Button from './Button.vue'
export default ({
  name: 'Header',
  components:{
    Button,
  },
  props:{
    title: String
  },
  data(){
    return {
      
    }
  },
  
})
</script>

<style scoped>
   header{
     color:#5f5f5f;
     border-radius: 5px;
     font-family: 'Roboto', sans-serif;
     font-weight: 500;
     text-transform: capitalize;
     display: flex;
     align-items: center;
     justify-content: space-between;
     max-width: 90%;
     margin: 20px auto;
     
   }
  
</style>
