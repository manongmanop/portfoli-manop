<script setup>
import { defineProps } from 'vue'
defineProps({
  location: String
})
</script>

<template>
  <div class="map-card">
    <div class="info">
      <span class="sub">สถานที่ทำงานปัจจุบัน</span>
      <h3 class="city">{{ location }}</h3>
    </div>
  </div>
</template>

<style scoped>
.map-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  gap: 0.6rem;
}

@keyframes ripple {
  0% { transform: scale(0.6); opacity: 1; }
  100% { transform: scale(1.4); opacity: 0; }
}

.sub {
  font-size: 0.7rem;
  letter-spacing: 0.08em;
  color: #71717a;
  font-weight: 600;
}

.city {
  font-size: 1.15rem;
  color: #f4f4f5;
  margin: 0.25rem 0 0 0;
  font-weight: 600;
}
</style>