<script setup>
import { defineProps, defineEmits } from 'vue'
defineProps({
  socials: Object
})
const emit = defineEmits(['open-email'])
</script>

<template>
  <div class="sw-col">
    <div class="social-wrapper">
      <span class="sub">ติดต่อ</span>
      <div class="link-group">
        <button type="button" @click="emit('open-email')" class="social-btn email-btn">
          <span>✉️ Email</span>
        </button>
        <a :href="socials?.github" target="_blank" rel="noopener noreferrer" class="social-btn github-btn">
          <span>💻 GitHub</span>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sw-col,
.social-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  gap: 0.85rem;
}

.sub {
  font-size: 0.8rem;
  color: #a1a1aa;
  font-weight: 600;
}

.link-group {
  display: flex;
  flex-direction: row;
  gap: 0.65rem;
  width: 100%;
}

.social-btn {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.45rem;
  padding: 0.7rem 0.75rem;
  border-radius: 12px;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  text-decoration: none;
  transition: all 0.2s ease;
}

.email-btn {
  background: rgba(239, 68, 68, 0.08);
  border: 1px solid rgba(239, 68, 68, 0.4);
  color: #f87171;
}
.email-btn:hover {
  background: rgba(239, 68, 68, 0.16);
  transform: translateY(-2px);
}

.github-btn {
  background: rgba(34, 197, 94, 0.08);
  border: 1px solid rgba(34, 197, 94, 0.4);
  color: #4ade80;
}
.github-btn:hover {
  background: rgba(34, 197, 94, 0.16);
  transform: translateY(-2px);
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
@keyframes slideUp {
  from { transform: translateY(12px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}
</style>