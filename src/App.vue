<script setup>
import { ref, computed } from 'vue'

const newTodo = ref('')
const todos = ref([
  { id: 1, text: 'Vue 3の学習を進める', completed: true },
  { id: 2, text: 'モダンで美しいTODOアプリを作る', completed: false },
  { id: 3, text: 'CSSのアニメーションをマスターする', completed: false }
])

const filter = ref('all') // 'all', 'active', 'completed'

const filteredTodos = computed(() => {
  if (filter.value === 'active') {
    return todos.value.filter(todo => !todo.completed)
  } else if (filter.value === 'completed') {
    return todos.value.filter(todo => todo.completed)
  }
  return todos.value
})

const addTodo = () => {
  if (newTodo.value.trim() !== '') {
    todos.value.unshift({
      id: Date.now(),
      text: newTodo.value,
      completed: false
    })
    newTodo.value = ''
  }
}

const toggleTodo = (todo) => {
  todo.completed = !todo.completed
}

const deleteTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}
</script>

<template>
  <div class="todo-app">
    <div class="glass-panel">
      <header>
        <h1>Task Master</h1>
        <p class="subtitle">美しく、効率的にタスクを管理</p>
      </header>

      <div class="input-group">
        <input 
          v-model="newTodo" 
          @keyup.enter="addTodo"
          type="text" 
          placeholder="新しいタスクを追加..." 
          class="todo-input"
        />
        <button @click="addTodo" class="add-btn">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"></line><line x1="5" y1="12" x2="19" y2="12"></line></svg>
        </button>
      </div>

      <div class="filters">
        <button :class="{ active: filter === 'all' }" @click="filter = 'all'">すべて</button>
        <button :class="{ active: filter === 'active' }" @click="filter = 'active'">進行中</button>
        <button :class="{ active: filter === 'completed' }" @click="filter = 'completed'">完了</button>
      </div>

      <TransitionGroup name="list" tag="ul" class="todo-list">
        <li v-for="todo in filteredTodos" :key="todo.id" class="todo-item" :class="{ completed: todo.completed }">
          <label class="checkbox-container">
            <input type="checkbox" :checked="todo.completed" @change="toggleTodo(todo)">
            <span class="checkmark"></span>
          </label>
          <span class="todo-text">{{ todo.text }}</span>
          <button @click="deleteTodo(todo.id)" class="delete-btn" aria-label="Delete todo">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"></path><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"></path><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"></path><line x1="10" y1="11" x2="10" y2="17"></line><line x1="14" y1="11" x2="14" y2="17"></line></svg>
          </button>
        </li>
      </TransitionGroup>

      <div v-if="filteredTodos.length === 0" class="empty-state">
        <p>タスクがありません。素晴らしい1日を！</p>
      </div>
    </div>
  </div>
</template>