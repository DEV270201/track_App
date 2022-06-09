<template>
<div class="w-full flex flex-col items-center h-[250px] overflow-y-scroll my-4">
  <div class="w-10/12 p-2" v-for="task in tasks" :key="task.id">
     <NewTask @delete_Task="$emit('delete_task',task.id)" :task="task.task" :date="task.date"/> 
  </div>
</div>
</template>

<script>
import NewTask from "../components/NewTask"
   export default{
       name:'MyTasks',
       props : {
           tasks : {
               type: Array
           }
       },
       components : {
           NewTask
       }
   }
</script>