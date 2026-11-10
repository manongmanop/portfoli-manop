<script setup>
import { defineProps } from 'vue'
defineProps({
  skills: Array
})
const getSkillColor = (skillName) => {
  const name = skillName.toLowerCase()
  if (name.includes('vue') || name.includes('mongo')) return 'chip-green'
  if (name.includes('react') || name.includes('tailwind') ) return 'chip-blue'
  if (name.includes('javascript') || name.includes('js') || name.includes('sql')) return 'chip-yellow'
  return 'chip-purple'
}
</script>

<template>
  <div class="tech-wrapper">
    <span class="sub">พื้นฐานสกิล</span>
    <div class="stack-cloud">
      <div 
      v-for="skill in skills" 
      :key="skill" class="tech-chip"
      :class="getSkillColor(skill)">
        {{ skill }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.tech-wrapper {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.sub {
  font-size: 0.7rem;
  letter-spacing: 0.08em;
  color: #71717a;
  font-weight: 600;
}

.stack-cloud {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-chip {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.07);
  padding: 0.4rem 0.75rem;
  border-radius: 10px;
  font-size: 0.825rem;
  color: #e4e4e7;
  transition: all 0.2s ease;
}

.tech-chip:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(255, 255, 255, 0.15);
  transform: translateY(-1px);
}
.chip-green {
  background: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.35);
  color: #4ade80;
}
.chip-green:hover {
  border-color: #22c55e;
}
.chip-blue {
  background: rgba(56, 189, 248, 0.1);
  border: 1px solid rgba(56, 189, 248, 0.35);
  color: #38bdf8;
}
.chip-blue:hover {
  border-color: #0ea5e9;
}
.chip-yellow {
  background: rgba(234, 179, 8, 0.1);
  border: 1px solid rgba(234, 179, 8, 0.35);
  color: #facc15;
}
.chip-yellow:hover {
  border-color: #eab308;
}
.chip-purple {
  background: rgba(168, 85, 247, 0.1);
  border: 1px solid rgba(168, 85, 247, 0.35);
  color: #c084fc;
}
.chip-purple:hover {
  border-color: #a855f7;
}
</style>