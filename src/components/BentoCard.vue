<script setup>
import { ref } from 'vue'

const cardRef = ref(null)
const mouseX = ref(0)
const mouseY = ref(0)
const isHovered = ref(false)

const handleMouseMove = (e) => {
  if (!cardRef.value) return
  const rect = cardRef.value.getBoundingClientRect()
  mouseX.value = e.clientX - rect.left
  mouseY.value = e.clientY - rect.top
}
</script>

<template>
  <div 
    ref="cardRef"
    class="bento-card"
    @mousemove="handleMouseMove"
    @mouseenter="isHovered = true"
    @mouseleave="isHovered = false"
  >
    <!-- Spotlight Glow Layer -->
    <div 
      class="spotlight"
      :style="{
        opacity: isHovered ? 1 : 0,
        background: `radial-gradient(400px circle at ${mouseX}px ${mouseY}px, rgba(255, 255, 255, 0.06), transparent 80%)`
      }"
    ></div>

    <div class="card-inner">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.bento-card {
  position: relative;
  background: rgba(18, 18, 20, 0.75);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 24px;
  overflow: hidden;
  transition: border-color 0.3s ease, transform 0.2s ease;
}

.bento-card:hover {
  border-color: rgba(255, 255, 255, 0.18);
}

.spotlight {
  pointer-events: none;
  position: absolute;
  inset: 0;
  transition: opacity 0.3s ease;
}

.card-inner {
  position: relative;
  z-index: 1;
  height: 100%;
  padding: 1.75rem;
  display: flex;
  flex-direction: column;
}
</style>