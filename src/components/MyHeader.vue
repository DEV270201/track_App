<template>
<div class="w-full flex flex-row justify-between px-4 py-4 items-center my-4">
   <h2 class="text-center text-xl">Task Track</h2>
   <button @click="addTask" class="w-[100px] rounded-lg p-2 bg-dark-200 hover:bg-light-200 text-light-200 hover:text-dark-200">Add Task</button>
</div>
</template>

<script>
  export default{
     name : 'MyHeader',
     methods : {
        addTask(){
           console.log("task added..")
        }
     }
  }
</script>