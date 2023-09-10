<script setup lang="ts">
  const tasks = localStorage.getItem('tasks')
</script>

<template>
  <table v-if="tasks">
    <tr v-for="task in tasks"></tr>
  </table>
  <h1 v-else>no</h1>
</template>

<style scoped>

</style>