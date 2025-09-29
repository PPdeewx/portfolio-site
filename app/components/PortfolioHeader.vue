<template>
  <header class="header">
    <h1 class="name">Pakphum Siliwattanakul</h1>
    <h2 class="role">Software Engineer | Frontend & Backend Developer</h2>
    <p class="tagline">
      Passionate about building scalable software.
    </p>
    <div class="socials">
      <a href="mailto:ken.24112547@gmail.com">✉ Email</a>
      <a href="https://github.com/PPdeewx" target="_blank">💻 GitHub</a>
      <a href="https://www.linkedin.com/in/pakphum-siliwattanakul-093a22193/" target="_blank">🔗 LinkedIn</a>
    </div>
  </header>
</template>

<style scoped>
.header {
  text-align: center;
  padding: 60px 20px;
  background: linear-gradient(135deg, #1e3a8a, #3b82f6);
  color: white;
  border-radius: 12px;
  margin-bottom: 40px;
  animation: fadeIn 1s ease-in;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
.name {
  font-size: 2.8rem;
  font-weight: 700;
}
.role {
  font-size: 1.3rem;
  margin: 12px 0;
}
@media (max-width: 768px) {
  .name { font-size: 2rem; }
  .role { font-size: 1.1rem; }
}
.tagline {
  font-size: 1rem;
  opacity: 0.9;
}
.socials {
  margin-top: 15px;
}
.socials a {
  margin: 0 10px;
  color: white;
  text-decoration: none;
  font-weight: bold;
}
.socials a:hover {
  text-decoration: underline;
}
</style>
