<template>
<div class="h-screen flex justify-center items-center">
  <div class="xs:w-3/4 lg:w-5/12 h-auto border-2 border-stone-800 rounded">
    <MyHeader />
    <AddTask @addNewTask="addNewTask"/>
    <MyTasks :tasks="tasks" @delete_task="deleteMyTask"/>
  </div>
</div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyTasks from "./components/MyTasks.vue"
import AddTask from "./components/AddTask.vue"

export default {
  name: 'App',
  components: {
    MyHeader,
    MyTasks,
    AddTask
},
  data(){
    return{
      tasks : []
    }
  },
  created(){
    console.log("created...");
     this.tasks = [
       {
         id : 1,
         task : 'Go to the shopping mall',
         date :  '31/06/2021'
       },
        {
         id : 2,
         task : 'Morning walk @7:30 AM',
         date :  '31/06/2021'

       },
        {
         id : 3,
         task : 'Complete reading the book',
         date : '31/06/2021'
       }
     ]
  },
  methods:{
    deleteMyTask(id){
      // console.log("id : ",id);
      if(confirm("Are you sure??")){
        this.tasks = this.tasks.filter((val)=>{
           return val.id !== id
        });
      }
    },
    addNewTask(task){
      this.tasks = [...this.tasks,task];
    }
  }
}
</script>

