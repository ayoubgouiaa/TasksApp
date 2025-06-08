<script setup>
    import {ref} from 'vue'
    const newTask=ref("")

    const props=defineProps({
        n_done:{
            type:Number,
            required:true
        },
        tasks:{
            type:Array,
            required:true
        }
      
    })
    const emit=defineEmits(['add-task'])
    function addTask(){
        if (newTask.value.trim()){
            emit('add-task',newTask.value)
            newTask.value=""
        }
        
    }
    
</script>


<template>
    <main>
    <h1>Tasks App</h1>
    <br>
    <div>
      <form @submit.prevent="addTask">
        <label>
          NewTask
          <input v-model="newTask" name="NewTask">
        </label>
        <button type="submit">Add Task</button>
        <br>
        <div v-if="!tasks.length">Let's Get started , Add you first Task !</div>
        <div v-else>You have {{ n_done }} / {{ tasks.length }} Tasks Done</div>
      </form>
      
    </div>
    </main>

</template>
