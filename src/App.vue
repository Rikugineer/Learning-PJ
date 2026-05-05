<script setup>
// ここから下にVueのロジックを自分で実装してみましょう！
// 例: import { ref } from 'vue'
</script>

<template>
  <div class="todo-app">
    <div class="glass-panel">
      <header>
        <h1>Task Master</h1>
        <p class="subtitle">美しく、効率的にタスクを管理</p>
      </header>

      <!-- 入力エリア -->
      <div class="input-group">
        <input 
          type="text" 
          placeholder="新しいタスクを追加..." 
          class="todo-input"
        />
        <button class="add-btn">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"></line><line x1="5" y1="12" x2="19" y2="12"></line></svg>
        </button>
      </div>

      <!-- フィルター -->
      <div class="filters">
        <button class="active">すべて</button>
        <button>進行中</button>
        <button>完了</button>
      </div>

      <!-- タスクリスト -->
      <ul class="todo-list">
        <!-- 完了済みのタスク例 -->
        <li class="todo-item completed">
          <label class="checkbox-container">
            <input type="checkbox" checked>
            <span class="checkmark"></span>
          </label>
          <span class="todo-text">Vue 3の学習を進める</span>
          <button class="delete-btn" aria-label="Delete todo">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"></path><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"></path><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"></path><line x1="10" y1="11" x2="10" y2="17"></line><line x1="14" y1="11" x2="14" y2="17"></line></svg>
          </button>
        </li>

        <!-- 未完了のタスク例 -->
        <li class="todo-item">
          <label class="checkbox-container">
            <input type="checkbox">
            <span class="checkmark"></span>
          </label>
          <span class="todo-text">モダンで美しいTODOアプリを作る</span>
          <button class="delete-btn" aria-label="Delete todo">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"></path><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"></path><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"></path><line x1="10" y1="11" x2="10" y2="17"></line><line x1="14" y1="11" x2="14" y2="17"></line></svg>
          </button>
        </li>

        <!-- 未完了のタスク例2 -->
        <li class="todo-item">
          <label class="checkbox-container">
            <input type="checkbox">
            <span class="checkmark"></span>
          </label>
          <span class="todo-text">CSSのアニメーションをマスターする</span>
          <button class="delete-btn" aria-label="Delete todo">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"></path><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"></path><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"></path><line x1="10" y1="11" x2="10" y2="17"></line><line x1="14" y1="11" x2="14" y2="17"></line></svg>
          </button>
        </li>
      </ul>

      <!-- タスクが空の場合の表示例（必要に応じて使用してください） -->
      <!--
      <div class="empty-state">
        <p>タスクがありません。素晴らしい1日を！</p>
      </div>
      -->
    </div>
  </div>
</template>