<script setup lang="ts">
import { ref } from 'vue'

interface Task {
  name: string
  is_finished: boolean
}

const tasks = ref<Task[]>([])
const newTaskName = ref('')
const TaskState = ref(false)
const addTasks = () => {
  tasks.value.push({ name: newTaskName.value, is_finished: TaskState.value })
}
</script>

<template>
  <div>
    <ul>
      <div>未完了のタスク</div>
      <template v-for="task in tasks" :key="task.name">
        <li v-if="task.is_finished == false">
          <div>名前: {{ task.name }}</div>
          <button @click="task.is_finished = true">完了</button>
        </li>
      </template>
      <div>完了したタスク</div>
      <template v-for="task in tasks" :key="task.name">
        <li v-if="task.is_finished == true">
          <div>名前: {{ task.name }}</div>
          <button @click="task.is_finished = true">完了</button>
        </li>
      </template>
    </ul>
    <div>
      <label>
        タスク名
        <input v-model="newTaskName" type="text" />
      </label>
      <button @click="addTasks">追加</button>
    </div>
  </div>
</template>

<style>
.over500 {
  color: red;
}
</style>
