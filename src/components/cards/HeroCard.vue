<script setup>
import { defineProps } from 'vue'
import myAvatar from '@/assets/Profile.png'

defineProps({
  name: String,
  nickname: String,
  role: String,
  bio: String
})
</script>

<template>
  <div class="hero-full-bleed">
    <!-- รูปภาพพื้นหลังเต็มการ์ด -->
    <img :src="myAvatar" alt="Profile" class="bg-image" />
    
    <!-- เลเยอร์ไล่สีดำจากล่างขึ้นบนเพื่อให้ตัวหนังสืออ่านง่าย -->
    <div class="gradient-overlay"></div>

    <!-- เนื้อหาที่ลอยอยู่ด้านบนรูป -->
    <div class="overlay-content">
      <div class="top-row">
        <div class="availability-badge">
          <span class="dot"></span>
          <span>Junior Software Engineer</span>
        </div>
      </div>

      <div class="intro">
        <h1 class="name">{{ name }} <span class="dim">({{ nickname }})</span></h1>
        <p class="role">{{ role }}</p>
        <p class="desc">{{ bio }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.hero-full-bleed {
  position: relative;
  /* ดึงออกให้ชิดขอบการ์ด BentoCard (ชดเชย padding 1.75rem ของ BentoCard) */
  margin: -1.75rem;
  padding: 1.75rem;
  height: calc(100% + 3.5rem);
  min-height: 360px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  overflow: hidden;
  border-radius: 24px;
}

.bg-image {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 20%;
  z-index: 0;
}

.gradient-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(9, 9, 11, 0.95) 25%,
    rgba(9, 9, 11, 0.5) 65%,
    rgba(9, 9, 11, 0.2) 100%
  );
  z-index: 1;
}

.overlay-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}

.top-row {
  display: flex;
  justify-content: flex-end;
}

.availability-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(9, 9, 11, 0.75);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(34, 197, 94, 0.3);
  color: #4ade80;
  font-size: 0.75rem;
  padding: 0.35rem 0.75rem;
  border-radius: 9999px;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #22c55e;
  box-shadow: 0 0 8px #22c55e;
}

.name {
  font-size: 1.85rem;
  font-weight: 700;
  color: #ffffff;
  margin: 0 0 0.25rem 0;
}

.dim {
  color: #a1a1aa;
  font-weight: 400;
}

.role {
  font-size: 1rem;
  color: #38bdf8;
  margin: 0 0 0.75rem 0;
  font-weight: 500;
}

.desc {
  font-size: 0.95rem;
  color: #e4e4e7;
  line-height: 1.6;
  margin: 0;
}
</style>