<script setup>
import TaskForm from './components/TaskForm.vue'
import TasksList from './components/TasksList.vue'
import {ref,computed} from 'vue'
const tasks = ref([])
function markDone(index){
  if(!tasks.value[index].done){
    tasks.value[index].done=true
  }
}
function rmTask(index){
  tasks.value.splice(index,1)
}

const n_done = computed(() => {
  return tasks.value.filter(task => task.done).length
})


function addTask(newTask) {
  tasks.value.push({
    task:newTask,
    done:false
  })
}
</script>

<template>
  <TaskForm @add-task="addTask" :tasks="tasks" :n_done="n_done"/>
  <TasksList :tasks="tasks" @mark-done="markDone" @remove-task="rmTask"/>
</template>
<style>
main{
  max-width: 800px;
  margin: 2rem auto;
}
</style>


