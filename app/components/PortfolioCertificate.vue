<template>
  <div class="certificates-section">
    <p class="subtitle">Certificates earned during study and courses</p>

    <div class="certificates-grid">
      <div class="certificate-card" v-for="(c, idx) in certificates" :key="idx">
        <h3>{{ c.title }}</h3>
        <p>{{ c.description }}</p>
        <div class="certificate-images">
          <img v-for="(img, i) in c.images" :key="i" :src="img" :alt="c.title + ' image ' + (i+1)" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const certificates = [
  {
    images: [
      "/images/Cer1.png",
      "/images/Cer2.png",
      "/images/Cer3.png"
    ]
  }
]
</script>

<style scoped>
.certificates-section {
  margin-top: 24px;
}

.section-title {
  font-size: 1.5rem;
  color: #0f172a;
  margin-bottom: 6px;
}

.subtitle {
  color: #475569;
  margin-bottom: 18px;
}

.certificates-grid {
  display: grid;
  gap: 24px;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
}

.certificate-card {
  background: white;
  padding: 16px;
  border-radius: 12px;
  box-shadow: 0 6px 18px rgba(2,6,23,0.06);
  display: flex;
  flex-direction: column;
}
.certificate-card:hover {
  transform: translateY(-5px);
}

.certificate-card h3 {
  margin: 0;
  color: #0f172a;
  font-size: 1.05rem;
}

.certificate-card p {
  margin: 0;
  color: #64748b;
  font-size: 0.9rem;
}

.certificate-images {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
}

.certificate-images img {
  width: 100%;
  max-width: 430px;
  border-radius: 8px;
  object-fit: cover;
}
.certificate-images img:hover {
  transform: scale(1.05);
}
</style>
