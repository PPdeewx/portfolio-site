<template>
  <section class="about-section">
    <div class="about-content">
      <img src="/images/profile.jpg" alt="Pakphum Siliwattanakul Profile" class="profile-img" />
      <div class="about-text">
        <p class="about-description">
          I'm a third-year Software Engineering student at University of Phayao with a strong interest in programming, IT systems, and software development. Eager to gain hands-on experience, develop technical skills, and contribute to a professional team. Responsible, fast learner, and a team player.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  margin: 40px 0;
  padding: 20px;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.about-content {
  display: flex;
  align-items: flex-start;
  gap: 20px;
}

.profile-img {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid #ffffff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
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

.about-description {
  font-size: 1rem;
  color: #334155;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .about-content {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .profile-img {
    width: 120px;
    height: 120px;
    margin-bottom: 15px;
  }

  .section-title {
    font-size: 1.5rem;
  }
}
</style>