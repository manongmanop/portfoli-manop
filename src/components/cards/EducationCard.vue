<script setup>
import { defineProps } from 'vue'

defineProps({
  education: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="edu-card">
    <div class="top-header">
      <span class="sub">การศึกษา</span>
      <span class="grad-year">{{ education.year }}</span>
    </div>

    <div class="edu-body">
      <div class="icon-box">🎓</div>
      <div>
        <h3 class="degree">{{ education.degree }}</h3>
        <p class="major">{{ education.major }}</p>
        <p class="uni">{{ education.university }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.edu-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  gap: 1rem;
}

.top-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sub {
  font-size: 0.7rem;
  letter-spacing: 0.08em;
  color: #71717a;
  font-weight: 600;
}

.grad-year {
  font-size: 0.75rem;
  color: #38bdf8;
  background: rgba(56, 189, 248, 0.1);
  border: 1px solid rgba(56, 189, 248, 0.2);
  padding: 0.2rem 0.6rem;
  border-radius: 9999px;
}

.edu-body {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.icon-box {
  font-size: 1.75rem;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  width: 48px;
  height: 48px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.degree {
  font-size: 1.05rem;
  font-weight: 700;
  color: #f4f4f5;
  margin: 0 0 0.2rem 0;
}

.major {
  font-size: 0.9rem;
  color: #22c55e;
  font-weight: 500;
  margin: 0 0 0.2rem 0;
}

.uni {
  font-size: 0.85rem;
  color: #a1a1aa;
  margin: 0;
}
</style>