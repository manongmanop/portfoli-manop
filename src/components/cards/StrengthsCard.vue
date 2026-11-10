<script setup>
import { defineProps } from 'vue'

defineProps({
  strengths: {
    type: Array,
    required: true
  },
  weaknesses: {
    type: Array,
    default: () => []
  }
})
</script>

<template>
  <div class="sw-card">
    <!-- ฝั่งซ้าย: จุดแข็ง -->
    <div class="sw-col">
      <span class="sub strength-title">⚡   จุดแข็ง </span>
      <ul class="sw-list">
        <li v-for="(item, index) in strengths" :key="index" class="sw-item strength-box">
          <span class="icon">✦</span>
          <span>{{ item }}</span>
        </li>
      </ul>
    </div>

    <!-- ฝั่งขวา: จุดด้อย -->
    <div class="sw-col">
      <span class="sub weakness-title">🔧   จุดด้อย </span>
      <ul class="sw-list">
        <li v-for="(item, index) in weaknesses" :key="index" class="sw-item weakness-box">
          <span class="icon">•</span>
          <span>{{ item }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.sw-card {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  height: 100%;
  align-items: stretch;
}

.sw-col {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  height: 100%;
}

.sub {
  font-size: 0.72rem;
  letter-spacing: 0.06em;
  font-weight: 700;
}

.strength-title {
  color: #38bdf8;
}

.weakness-title {
  color: #fbbf24;
}

.sw-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
  flex: 1;
}

.sw-item {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.875rem;
  color: #e4e4e7;
  padding: 0.65rem 0.85rem;
  border-radius: 12px;
  line-height: 1.5;
}

.strength-box {
  background: rgba(56, 189, 248, 0.05);
  border: 1px solid rgba(56, 189, 248, 0.15);
}
.strength-box .icon {
  color: #38bdf8;
}

.weakness-box {
  background: rgba(251, 191, 36, 0.05);
  border: 1px solid rgba(251, 191, 36, 0.15);
}
.weakness-box .icon {
  color: #fbbf24;
}

@media (max-width: 640px) {
  .sw-card {
    grid-template-columns: 1fr;
  }
}
</style>