<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const username = ref('')

onMounted(() => {
  const storedUsername = localStorage.getItem('username')
  if (!storedUsername) {
    router.push('/login')
  } else {
    username.value = storedUsername
  }
})

const handleLogout = () => {
  localStorage.removeItem('username')
  router.push('/login')
}
</script>

<template>
  <div class="matching-container">
    <header class="header">
      <h1>💖 Find Your Match</h1>
      <button @click="handleLogout" class="btn-logout">Logout</button>
    </header>

    <main class="content">
      <div class="placeholder">
        <h2>Welcome, {{ username }}!</h2>
        <p>Matching functionality coming soon...</p>
        <div class="icon">🔍</div>
      </div>
    </main>
  </div>
</template>

<style scoped>
.matching-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.header {
  background: rgba(255, 255, 255, 0.95);
  padding: 1.5rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.header h1 {
  margin: 0;
  font-size: 1.75rem;
  color: #333;
}

.btn-logout {
  padding: 0.625rem 1.5rem;
  background: white;
  color: #667eea;
  border: 2px solid #667eea;
  border-radius: 0.5rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
}

.btn-logout:hover {
  background: #667eea;
  color: white;
}

.content {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 5rem);
  padding: 2rem;
}

.placeholder {
  background: white;
  border-radius: 1rem;
  padding: 3rem;
  text-align: center;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  max-width: 500px;
}

.placeholder h2 {
  margin: 0 0 1rem 0;
  color: #333;
  font-size: 2rem;
}

.placeholder p {
  margin: 0 0 2rem 0;
  color: #666;
  font-size: 1.125rem;
}

.icon {
  font-size: 4rem;
  opacity: 0.3;
}
</style>
