<template>
    <div class="flex justify-center">
        <div class="w-10/12 flex flex-col items-center bg-dark-200 rounded-xl p-4">
            <label class="block w-3/4">
                <input
                    class="placeholder:text-dark-300 block bg-light-200 w-full border border-slate-300 rounded-md py-2 pl-4 pr-3 shadow-lg focus:outline-none sm:text-sm"
                    placeholder="Add Your Task..." type="text" name="task" v-model="task">
            </label>
            <label class="block w-3/4 my-3">
                <input
                    class="placeholder:text-dark-300 block bg-light-200 w-full border border-slate-300 rounded-md py-2 pl-4 pr-3 shadow-lg focus:outline-none sm:text-sm"
                    placeholder="Add Date..." type="date" name="date" v-model="date">
            </label>
            <button @click="saveTask"
                class="w-3/4 rounded-lg p-2 hover:bg-dark-200 bg-light-200 hover:text-light-200 text-dark-200">Save
                Task</button>

        </div>
    </div>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            task: '',
            date: ''
        }
    },
    methods: {
        saveTask() {
            if(this.task.trim() === ''){
                alert("please enter the task properly");
                return;
            }
            console.log(typeof(this.date))
            if(!this.date){
                alert("please enter the date properly");
                return;
            }
            const newTask = {
                task : this.task,
                date :  new Date(this.date).toLocaleDateString("en-GB", {
                year: "numeric",
                month: "2-digit",
                day: "2-digit",
            })
            }
            
            //emitting the object to the parent
            this.$emit('addNewTask',newTask);

            //clearing the input fields
            this.task = "";
            this.date = "";
        }
    }
}
</script>