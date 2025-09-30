<template>
  <div class="portfolio-container">

    <nav class="nav-bar">
      <div class="nav-logo">
        <h1>Pakphum Siliwattanakul</h1>
      </div>
      <ul class="nav-links">
        <li><a href="#aboutme" class="nav-link">AboutMe</a></li>
        <li><a href="#education" class="nav-link">Education</a></li>
        <li><a href="#projects" class="nav-link">Projects</a></li>
        <li><a href="#skills" class="nav-link">Skills</a></li>
        <li><a href="#certificates" class="nav-link">Certificates</a></li>
        <li><a href="#contact" class="nav-link">Contact</a></li>
      </ul>
    </nav>

    <PortfolioHeader />

    <section id="aboutme" class="section">
      <h2 class="section-title">AboutMe</h2>
      <PortfolioAboutMe />
    </section>

    <section id="education" class="section">
      <h2 class="section-title">Education</h2>
      <PortfolioEducation />
    </section>

    <section id="projects" class="section">
      <h2 class="section-title">Projects</h2>
      <PortfolioProjects />
    </section>

    <section id="skills" class="section">
      <h2 class="section-title">Skills</h2>
      <PortfolioSkills />
    </section>

    <section id="certificates" class="section">
      <h2 class="section-title">Certificates</h2>
      <PortfolioCertificate />
    </section>

    <section id="contact" class="section">
      <h2 class="section-title">Contact</h2>
      <PortfolioContact />
    </section>

    <footer class="footer">
      <p>&copy; 2025 Pakphum Siliwattanakul. All rights reserved.</p>
    </footer>
  </div>
</template>

<style scoped>
.portfolio-container {
  max-width: 1500px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Inter', sans-serif;
  background-color: #f8fafc;
  min-height: 100vh;
}

.nav-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  background: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  border-radius: 8px;
  position: sticky;
  top: 0;
  z-index: 1000;
}

.nav-logo h1 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #1e3a8a;
}

.nav-links {
  display: flex;
  gap: 20px;
  list-style: none;
}

.nav-link {
  color: #1e3a8a;
  text-decoration: none;
  font-weight: 500;
  font-size: 1rem;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #3b82f6;
}

.section {
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

.footer {
  text-align: center;
  padding: 20px;
  color: #64748b;
  font-size: 0.9rem;
  border-top: 1px solid #e2e8f0;
  margin-top: 40px;
}

@media (max-width: 768px) {
  .nav-bar {
    flex-direction: column;
    gap: 10px;
  }

  .nav-links {
    flex-direction: column;
    gap: 10px;
    text-align: center;
  }

  .section-title {
    font-size: 1.5rem;
  }
}
</style>