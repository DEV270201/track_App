<template>
<div>
<NavBar />
<div class="notif h-[50px] w-full fixed top-[50px]" :class="notif && 'show'">
  <NotiFications :msg="msg" :error="error"/>
</div>
<div class="h-screen flex justify-center items-center">
  <div class="xs:w-3/4 lg:w-5/12 h-auto border-2 border-stone-800 rounded mt-10">
    <MyHeader @toggle="toggle" :isOpen="isOpen" @showNotification="showNotification"/>
    <div v-if="isOpen">
      <AddTask @addNewTask="addNewTask" @showNotification="showNotification"/>
    </div>
    <MyTasks :tasks="tasks" @delete_task="deleteMyTask"/>
  </div>
</div>
</div>
</template>

<style>
  .notif{
    left: -100%;
    transition: 0.5s ease-in-out;
  }
  .show{
    left: 0%;
  }
</style>

<script>
import MyHeader from './components/MyHeader.vue'
import MyTasks from "./components/MyTasks.vue"
import AddTask from "./components/AddTask.vue"
import NavBar from './components/NavBar.vue'
import NotiFications from './components/NotiFications.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyTasks,
    AddTask,
    NavBar,
    NotiFications
},
  data(){
    return{
      tasks : [],
      isOpen : false,
      msg : "",
      error : false,
      notif : false
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
      this.showNotification("Task deleted successfully",false);
      }
    },
    addNewTask(task){
      this.tasks = [...this.tasks,task];
      this.showNotification("Task added successfully",false);
    },
    toggle(){
      this.isOpen = !this.isOpen;
    },
    showNotification(msg,err){
      console.log("msg : ",msg);
      console.log("err : ",err);
      this.msg = msg;
      this.error = err;
      this.notif = true;
      this.hideNotification();
    },
    hideNotification(){
      setTimeout(()=>{
         this.notif = false;
      },3000);
    }
  }
}
</script>

