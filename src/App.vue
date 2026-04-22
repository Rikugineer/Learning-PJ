<script setup>
// 【ロジック部】変数やデータを準備する場所
const name = "27歳 ITエンジニア"

// 学習ログのデータを「配列」として定義
// 1行に1件のデータ（ID、日付、内容）をまとめていて、管理しやすい形です
const logs = [
  { id: 1, date: "2026-04-22", content: "Node.jsをv24に更新し、Viteプロジェクトを立ち上げ" },
  { id: 2, date: "2026-04-21", content: "WSL2とGitの連携設定、GitHubへの初コミット" },
  { id: 3, date: "2026-04-20", content: "SRE/Cloudエンジニアに向けた学習ロードマップを作成" }
]
</script>

<template>
  <div class="portfolio">
    <header>
      <h1>{{ name }} のポートフォリオ</h1>
    </header>

    <main>
      <section class="profile">
        <h2>Profile</h2>
        <p>介護士からエンジニアへ。一人前のエンジニアを目指して学習中</p>
      </section>

      <section class="timeline">
        <h2>Learning Log</h2>
        <!-- v-forを使って「logs」配列のデータを1つずつ「log」として取り出し、繰り返し表示する -->
        <!-- :key="log.id" は、Vueが各項目を識別するための背番号（一意のキー） -->
        <div v-for="log in logs" :key="log.id" class="log-item">
          <!-- {{ }} を使うと、JavaScriptの変数をHTMLに表示できる -->
          <span class="log-date">{{ log.date }}</span> <!-- 日付を表示 -->
          <p class="log-text">{{ log.content }}</p> <!-- 内容を表示 -->
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
/* 【デザイン部】見た目を整える場所（CSS） */
.portfolio {
  font-family: sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  color: #333;
}
header {
  border-bottom: 2px solid #42b883; /* 下線の色 */
  margin-bottom: 20px;
}
h2 {
  color: #42b883; /* 見出しの色 */
}
.log-item {
  margin-bottom: 15px;
  padding: 10px;
  background: #f9f9f9; /* ログの背景色（薄いグレー） */
  border-radius: 8px; /* 角を少し丸くする */
}
.log-date {
  font-size: 0.8rem;
  color: #888;
  font-weight: bold;
}
.log-text {
  margin: 5px 0 0 0;
}
</style>