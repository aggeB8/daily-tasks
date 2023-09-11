<script setup lang="ts">
  import { ref, onMounted, watch } from 'vue'

    let tasks = ref<string[]>([])
    let newTask = ref('')

    function addTodo() {
        if (newTask.value.trim() === "") {
            return;
        }
        
        tasks.value.push(newTask.value)
        newTask.value = ''
    }

    watch(
        tasks,
        (newTodoValue) => {
            console.log(newTodoValue)
            localStorage.setItem("tasks", JSON.stringify(newTodoValue));
        },
        { deep: true }
    );

    onMounted(() => {
        tasks.value = JSON.parse(localStorage.getItem("tasks")!) || [];
    });
</script>

<template>
  <table>
    <tr>
      <th>Task</th>
      <th>Status</th>
    </tr>
    <tr v-for="task in tasks">
      <td>{{ task }}</td>
      <td>checkbox</td>
      <td>delete</td>
    </tr>
      

  </table>

  <div>
    <input v-model="newTask" type="text">
    <button @click="addTodo()">Create task</button>
  </div>
</template>

<style scoped>

</style>