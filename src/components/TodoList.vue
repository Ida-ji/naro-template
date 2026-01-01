<script setup lang="ts">
import { ref } from 'vue'

interface Todo {
  id: number
  task: string
}

const TodoList = ref<Todo[]>([

])

const finList = ref<Todo[]>([

])

let newtaskid = 1
const newtask = ref('')

const finish = (id: number) => {
  const index = TodoList.value.findIndex(todo => todo.id === id)
  if (index === -1) return

  const [finished] = TodoList.value.splice(index, 1)
  finList.value.push(finished)
}

const addtask = () => {
  if (newtask.value.trim() === '' ) {
    return
  }
  TodoList.value.push({id: newtaskid++, task: newtask.value})
  newtask.value = ''
}

const splicefintask = (id: number) => {
  const index2 = finList.value.findIndex(todo => todo.id === id)
  if (index2 === -1) return

  finList.value.splice(index2, 1)
}
</script>

<template>
  <div>
    <div>TodoList</div>
    <ul>
      <li v-for="Todo in TodoList" :key="Todo.id" >
        <div> {{ Todo.task }}</div>
        <button @click="finish(Todo.id)">完了</button>
      </li>
    </ul>
    <div>
      <label>
        名前
        <input v-model="newtask" type="text" />
      </label>
      <button @click="addtask">追加</button>
    </div>  

    <div>finList</div>
    <ul>
      <li v-for="Todo in finList" :key="Todo.id" >
        <div> {{ Todo.task }} </div>
        <button @click="splicefintask(Todo.id)">削除</button>
      </li>
    </ul>
  </div>
</template>

<style></style>