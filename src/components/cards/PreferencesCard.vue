<script setup>
import { defineProps } from 'vue'

defineProps({
 likes: {
    type: Array,
    default: () => []
  },
  dislikes: {
    type: Array,
    default: () => []
  }
})
</script>

<template>
  <div class="pref-card">
    <!-- ฝั่งซ้าย: สิ่งที่ชอบ -->
    <div class="pref-section">
      <div class="pref-header">
        <span class="badge-icon like-bg">👍</span>
        <span class="title like-text">สิ่งที่ชอบ</span>
      </div>

      <div class="items-grid">
        <div v-for="(item, i) in likes" :key="i" class="pref-box like-box">
          <span class="status-dot green"></span>
          <span class="item-text">{{ item }}</span>
        </div>
      </div>
    </div>

    <!-- เส้นคั่นกลาง -->
    <div class="vertical-divider"></div>

    <!-- ฝั่งขวา: สิ่งที่ไม่ชอบ -->
    <div class="pref-section">
      <div class="pref-header">
        <span class="badge-icon dislike-bg">👎</span>
        <span class="title dislike-text">สิ่งที่ไม่ชอบ</span>
      </div>

      <div class="items-grid">
        <div v-for="(item, i) in dislikes" :key="i" class="pref-box dislike-box">
          <span class="status-dot red"></span>
          <span class="item-text">{{ item }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.pref-card {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 2rem;
  height: 100%;
  align-items: stretch;
}

.pref-section {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.pref-header {
    display: flex;
    align-items: center;
    gap: 0.6rem;
}

.badge-icon {
    width: 28px;
    height: 28px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.85rem;
}

.like-bg {
  background: rgba(34, 197, 94, 0.12);
  border: 1px solid rgba(34, 197, 94, 0.25);
}

.dislike-bg {
  background: rgba(239, 68, 68, 0.12);
  border: 1px solid rgba(239, 68, 68, 0.25);
}

.title {
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.02em;
}

.like-text { color: #4ade80; }
.dislike-text { color: #f87171; }

.items-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
  gap: 0.65rem;
}

.pref-box {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  padding: 0.65rem 0.9rem;
  border-radius: 12px;
  font-size: 0.875rem;
  color: #e4e4e7;
  transition: all 0.2s ease;
}

.like-box {
  background: rgba(34, 197, 94, 0.04);
  border: 1px solid rgba(34, 197, 94, 0.14);
}

.like-box:hover {
  background: rgba(34, 197, 94, 0.1);
  border-color: rgba(34, 197, 94, 0.35);
  transform: translateY(-2px);
}

.dislike-box {
  background: rgba(239, 68, 68, 0.04);
  border: 1px solid rgba(239, 68, 68, 0.14);
}

.dislike-box:hover {
  background: rgba(239, 68, 68, 0.1);
  border-color: rgba(239, 68, 68, 0.35);
  transform: translateY(-2px);
}

.status-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  flex-shrink: 0;
}

.status-dot.green {
  background: #22c55e;
  box-shadow: 0 0 8px rgba(34, 197, 94, 0.6);
}

.status-dot.red {
  background: #ef4444;
  box-shadow: 0 0 8px rgba(239, 68, 68, 0.6);
}

.item-text {
  line-height: 1.4;
}

.vertical-divider {
  width: 1px;
  background: linear-gradient(
    to bottom,
    transparent,
    rgba(255, 255, 255, 0.1) 20%,
    rgba(255, 255, 255, 0.1) 80%,
    transparent
  );
}
/* 
.pref-col {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.pref-header {
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.08em;
}

.like-text { color: #4ade80; }
.dislike-text { color: #f87171; }

.pref-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.pref-list li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.875rem;
  color: #d4d4d8;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  flex-shrink: 0;
}

.dot.green { background: #22c55e; }
.dot.red { background: #ef4444; } */

@media (max-width: 500px) {
  .pref-card {
    grid-template-columns: 1fr;
  }
}
</style>