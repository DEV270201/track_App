<template>
  <div class="flex items-center justify-between bg-dark-200 text-light-200 rounded-xl py-2 px-4 hover:bg-light-200 hover:text-dark-200 hover:shadow-xl">
<div class="flex flex-col">
    <p>{{task}}</p>
    <p class="text-xs">{{date}}</p>
</div>
   <button @click="deleteTask" class="w-[100px] rounded-lg p-2 hover:bg-dark-200 bg-light-200 hover:text-light-200 text-dark-200">Delete</button>
  </div>
</template>

<script>
  export default{
      name : "NewTask",
      props : {
          task : {
              type : String
          },
          date : {
              type : String
          }
      },
      methods:{
          deleteTask(){
              this.$emit('delete_Task');
          }
      }
  }
</script>