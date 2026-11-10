<script setup>
import { defineProps } from 'vue'

defineProps({
  hobbies: Array,
  favoriteTeams: Array
})
</script>

<template>
  <div class="hobbies-card">
    <div class="section-block">
      <span class="sub">งานอดิเรก</span>
      <div class="pill-group">
        <span v-for="(hobby, i) in hobbies" :key="i" class="hobby-pill">
          {{ hobby }}
        </span>
      </div>
    </div>

    <div class="divider"></div>

    <div class="section-block">
      <span class="sub">ทีมโปรด ⚽</span>
      <div class="teams-row">
        <span v-for="(team, i) in favoriteTeams" :key="i" class="team-badge">
          🏆 {{ team }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.hobbies-card {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  gap: 1rem;
  height: 100%;
}

.section-block {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.sub {
  font-size: 0.7rem;
  letter-spacing: 0.08em;
  color: #71717a;
  font-weight: 600;
}

.pill-group, .teams-row {
  display: flex;
  flex-wrap: wrap;
  gap: 0.45rem;
}

.hobby-pill {
  font-size: 0.82rem;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  color: #d4d4d8;
  padding: 0.35rem 0.7rem;
  border-radius: 8px;
}

.team-badge {
  font-size: 0.85rem;
  font-weight: 600;
  background: rgba(239, 68, 68, 0.12);
  border: 1px solid rgba(239, 68, 68, 0.3);
  color: #fca5a5;
  padding: 0.45rem 0.85rem;
  border-radius: 10px;
}

.divider {
  height: 1px;
  background: rgba(255, 255, 255, 0.07);
  margin: 0.25rem 0;
}
</style>