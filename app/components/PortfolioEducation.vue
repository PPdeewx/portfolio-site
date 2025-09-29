<template>
  <section class="education-section">
    <div class="education-list">
      <div class="education-item">
        <h3 class="institution">University of Phayao</h3>
        <p class="degree">Software Engineering</p>
        <p class="duration">2023 - Present</p>
      </div>
      <div class="education-item">
        <h3 class="institution">Phetpittayakom School</h3>
        <p class="degree">IEP (Intensive English Program)</p>
        <p class="duration">2020 - 2023</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.education-section {
  margin: 40px 0;
  padding: 20px;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.section-title {
  font-size: 2rem;
  font-weight: 700;
  color: #1e3a8a;
  margin: 0 0 20px;
  position: relative;
  display: inline-block;
}

.section-title::after {
  content: '';
  width: 50%;
  height: 3px;
  background: #3b82f6;
  position: absolute;
  bottom: -5px;
  left: 0;
}

.education-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.education-item {
  background: #f8fafc;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.03);
}

.institution {
  font-size: 1.2rem;
  font-weight: 600;
  color: #1e3a8a;
  margin: 0 0 5px;
}

.degree {
  font-size: 1rem;
  color: #334155;
  margin: 0 0 5px;
}

.duration {
  font-size: 0.9rem;
  color: #64748b;
  margin: 0;
}

@media (max-width: 768px) {
  .section-title {
    font-size: 1.5rem;
  }

  .institution {
    font-size: 1.1rem;
  }
}
</style>