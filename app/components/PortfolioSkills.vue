<template>
  <div class="skills">
    <span v-for="skill in skills" :key="skill" class="skill-badge">{{ skill }}</span>
  </div>
</template>

<script setup>
const skills = [
  "Java", "Python", "Vue.js", "Nuxt", "Node.js",
  "HTML/CSS", "MySQL", "MongoDB", "Docker", "Git"
]
</script>

<style scoped>
.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.skill-badge {
  background: #f0f8ff;
  padding: 8px 12px;
  border-radius: 20px;
  font-size: 0.9rem;
  border: 1px solid #007bff;
  color: #007bff;
  font-weight: 500;
}
.skill-badge:hover {
  transform: scale(1.05);
  background: #dbeafe;
}
</style>
