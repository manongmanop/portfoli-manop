<template>
  <div class="space-app">
    <!-- Background Dot Pattern -->
    <div class="bg-dots"></div>

    <header class="top-nav">
      <div class="brand">Not.Space</div>
      <nav class="nav-pills">
        <router-link to="/" class="pill">Home</router-link>
      </nav>
    </header>

    <main class="main-content">
      <router-view />
    </main>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background-color: #09090b; /* โทนดำลึก */
  color: #f4f4f5;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
}
</style>

<style scoped>
.space-app {
  min-height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
}

.bg-dots {
  position: fixed;
  inset: 0;
  background-image: radial-gradient(rgba(255, 255, 255, 0.08) 1px, transparent 1px);
  background-size: 24px 24px;
  pointer-events: none;
  z-index: 0;
}

.top-nav {
  position: sticky;
  top: 1rem;
  z-index: 10;
  max-width: 960px;
  width: calc(100% - 2rem);
  margin: 1rem auto 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem 1.25rem;
  background: rgba(18, 18, 20, 0.7);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 9999px;
}

.brand {
  font-weight: 700;
  font-size: 0.95rem;
  letter-spacing: -0.02em;
}

.nav-pills {
  display: flex;
  gap: 0.5rem;
}

.pill {
  color: #a1a1aa;
  text-decoration: none;
  font-size: 0.85rem;
  padding: 0.35rem 0.85rem;
  border-radius: 9999px;
  transition: all 0.2s;
}

.pill:hover,
.router-link-active {
  color: #fff;
  background: rgba(255, 255, 255, 0.08);
}

.main-content {
  position: relative;
  z-index: 1;
  padding: 2.5rem 1rem 4rem;
  flex: 1;
}
</style>