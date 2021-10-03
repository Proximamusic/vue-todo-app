<template>
    <button :style="{'background-color': color}"   @click="$emit('toggleAddTask')">
        {{text}}
    </button>
</template>

<script>

export default({
   name: 'Button',
   props: {
      text : String,
      color: String
   },
   methods:{
      
   }
})
</script>


<style scoped>
   button{
       height: 40px;
       width: 100px;
       background-color: rgb(141, 141, 247);
       color: white;
       border: none;
       border-radius: 5px;
   }
</style>