<template>
  <div class="projects-section">
    <div class="projects-header">
      <p class="subtitle">Selected works during study and freelance — concise, responsive & production-ready</p>
    </div>

    <div class="projects-grid">
      <div class="project-card" v-for="(p, idx) in projects" :key="p.title">
        <div class="card-top">
          <div>
            <h3 class="project-title">{{ p.title }}</h3>
            <p class="project-sub">{{ p.brief }}</p>
          </div>
          <div class="tech">{{ p.tech }}</div>
        </div>

        <p class="desc">{{ p.shortDescription }}</p>

        <div class="card-actions">
          <a v-if="p.link" :href="p.link" target="_blank" class="btn-outline">🔗 Repo</a>
          <button class="btn-primary" @click="toggle(idx)">
            {{ expanded[idx] ? 'ปิดรายละเอียด' : 'ดูรายละเอียด' }}
          </button>
          <button v-if="p.images && p.images.length" class="btn-outline" @click="showGallery(idx)">
            📷 ดูรูป
          </button>
        </div>

        <transition name="fade">
          <div v-if="expanded[idx]" class="details">
            <h4>Overview</h4>
            <p v-if="p.longDescription">{{ p.longDescription }}</p>

            <h4>Key features</h4>
            <ul>
              <li v-for="(f, i) in p.features" :key="i">• {{ f }}</li>
            </ul>

            <h4>Roles</h4>
            <p>{{ p.roles }}</p>

            <h4>Notes</h4>
            <p v-if="p.notes">{{ p.notes }}</p>
          </div>
        </transition>
      </div>
    </div>

    <!-- Gallery Modal -->
    <div v-if="gallery.visible" class="gallery-overlay" @click.self="closeGallery">
      <div class="gallery-content">
        <button class="close-btn" @click="closeGallery">✖</button>
        <img :src="gallery.images[gallery.index]" :alt="'Project Image ' + (gallery.index + 1)" />
        <div class="gallery-nav">
          <button @click="prevImage" :disabled="gallery.index === 0">◀</button>
          <button @click="nextImage" :disabled="gallery.index === gallery.images.length - 1">▶</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const projects = [
  {
    title: "Artemis Shop (Second-hand E-commerce Web)",
    brief: "ร้านมือสองออนไลน์ UI สะอาด ใช้งานง่าย",
    shortDescription: "Vue.js + TailwindCSS, Firebase. การค้นหาและ filter, checkout flow",
    longDescription: "Store for second-hand items with search, filters and smooth checkout",
    tech: "Vue.js, TailwindCSS",
    link: "https://github.com/PPdeewx/artemisshop",
    roles: "Front-end Developer",
    notes: "",
    features: [
      "Responsive product listing, search & filters",
      "Simple cart & checkout"
    ],
    images: [
      "/images/Ar1.png",
      "/images/Ar2.png",
      "/images/Ar3.png",
      "/images/Ar4.png",
      "/images/Ar5.png",
      "/images/Ar6.png"
    ]
  },
  {
    title: "TaskHeroUP (Gamified To-do Web App)",
    brief: "Gamified to-do web app — เพิ่มแรงจูงใจด้วย reward & progress tracking",
    shortDescription: "Vue.js frontend + Node.js backend. มีระบบคะแนนและฮิสทอรีการทำงาน",
    longDescription: "ระบบจัดการงานแบบ gamification ที่เพิ่ม UX เพื่อกระตุ้นการใช้งานประจำวัน",
    tech: "Vue.js, Node.js, MongoDB",
    link: "https://github.com/PPdeewx/vue-todolist",
    roles: "Fullstack Developer",
    notes: "",
    features: [
      "Task CRUD, Reward system, Progress bar",
      "Authentication, Profile, Local storage sync"
    ],
    images: [
      "/images/Task1.png",
      "/images/Task2.png",
      "/images/Task3.png",
      "/images/Task4.png",
      "/images/Task5.png",
      "/images/Task6.png"
    ]
  },
  {
    title: "MisEte (Leave Management System Web App)",
    brief: "ระบบ MIS ศูนย์ ETE — ระบบจัดการการลา, วันหยุด, เวลางาน และการอนุมัติ",
    shortDescription: "Web application, responsive design. Roles: admin & user. พัฒนาด้วย Python, Vue.js, MariaDB, Docker.",
    longDescription: "ระบบสำหรับบริหารการลา และเวลางานของพนักงานภายในหน่วยงาน (Department-based approver, email notifications, time attendance import)",
    tech: "Python, Vue.js, MariaDB, Docker",
    link: "https://github.com/PPdeewx/dockermisete",
    roles: "Back-end Developer",
    notes: "รองรับการส่งอีเมลแจ้งเตือน, generate เลขที่เอกสาร (L-YYMMxxxx / W-YYMMxxxx), import เวลาเป็นไฟล์ Excel ตาม template",
    features: [
      "Department management (สร้าง, แก้ไข) — ระบุผู้อนุมัติได้หลายคน และห้ามลบหากมีพนักงานอยู่",
      "User management — สร้าง/แก้ไข/ค้นหา/กรอง (status, group, department), unique employee code & time attendance code",
      "Leave management — กำหนดโควต้าต่อปี, ขออนุมัติ, เลือกผู้อนุมัติ และผู้ปฏิบัติงานแทน, ส่ง email แจ้งผู้เกี่ยวข้อง",
      "Holiday management — Table & Calendar view, เพิ่มได้เป็นช่วง, ห้ามซ้ำ",
      "Work offsite requests — กระบวนการคล้ายการลา, มี W-YYMMxxxx, แจ้งผู้อนุมัติและผู้ร่วมงาน",
      "Time attendance — อัพโหลด Excel, คำนวณสาย/ออกก่อน, แสดงสรุปรายงานรายปี",
      "Admin approval queue — ตารางรายการรออนุมัติ พร้อมปุ่มอนุมัติ/ไม่อนุมัติ ส่งอีเมลผลลัพธ์",
      "Security/usability — ส่งอีเมลให้พนักงานตั้ง password ครั้งแรก, reset password แบบ self-service (complex 8 chars)"
    ],
    images: [
      "/images/Mis1.png",
      "/images/Mis2.png",
      "/images/Mis3.png",
      "/images/Mis4.png",
      "/images/Mis5.png",
      "/images/Mis6.png"
    ]
  },
  {
    title: "Attendance (Attendance Web App)",
    brief: "ระบบลงเวลาเข้า-ออกงานผ่านการกดหรือสแกนใบหน้า (Face Recognition) ภายในระยะไม่เกิน 200 เมตร",
    shortDescription: "Web app สำหรับลงเวลาเข้า-ออกพนักงาน รองรับสแกนใบหน้าและ location-based check-in พร้อมหน้าดูประวัติย้อนหลัง",
    longDescription: "Attendance Management System ที่ช่วยให้องค์กรสามารถบันทึกเวลาเข้า-ออกของพนักงานได้อย่างแม่นยำ โดยใช้ Vue.js เป็น frontend, Django เป็น backend API, และ PostgreSQL เป็นฐานข้อมูล รองรับการยืนยันตัวตนด้วย Face Recognition และตรวจสอบตำแหน่ง (geofencing ระยะ ≤200 เมตร) เพื่อป้องกันการลงเวลานอกพื้นที่ พร้อมมี dashboard และหน้าดูประวัติการลงเวลา",
    tech: "Vue.js, Django, PostgreSQL, Face Recognition API, Geolocation API",
    link: "https://github.com/PPdeewx/attendance-app",
    roles: "Fullstack Developer",
    notes: " user: admin / pass: adminpass, https://attendance-frontend-r4gw.onrender.com/, https://attendance-backend-v67b.onrender.com/,",
    features: [
        "Face Recognition หรือ Manual Check-in/out (กดปุ่ม) — ตรวจสอบตำแหน่งไม่เกิน 200 เมตรจากพื้นที่บริษัท",
        "Geofencing: ใช้ location-based validation ป้องกันการลงเวลานอกพื้นที่",
        "History Page: พนักงานดูประวัติการเข้างาน/ออกงานย้อนหลังได้ (Filter ตามวัน/เดือน/สถานะ)",
        "Admin Dashboard: ดูสรุปการเข้างานของพนักงานทั้งหมด, ออกรายงานเป็น Excel/PDF",
        "Database: บันทึกข้อมูลลง PostgreSQL, รองรับ scale สำหรับองค์กร",
        "Authentication & Role-based Access: User ลงเวลา, Admin จัดการพนักงานและตรวจสอบข้อมูล",
        "Notification/Alert: แจ้งเตือนเมื่อมีการลงเวลาสำเร็จหรือไม่สำเร็จ",
        "Responsive Design: ใช้งานได้ทั้ง desktop และ mobile"
    ],
    images: [
      "/images/A1.png",
      "/images/A2.png",
      "/images/A3.png",
      "/images/A4.png"
    ]
  }
]

const expanded = reactive(projects.map(() => false))

function toggle(index) {
  expanded[index] = !expanded[index]
}

const gallery = reactive({
  visible: false,
  images: [],
  index: 0
})

function showGallery(idx) {
  gallery.images = projects[idx].images
  gallery.index = 0
  gallery.visible = true
}

function closeGallery() {
  gallery.visible = false
}

function prevImage() {
  if (gallery.index > 0) gallery.index--
}

function nextImage() {
  if (gallery.index < gallery.images.length - 1) gallery.index++
}
</script>

<style scoped>
.projects-section {
  margin-top: 18px;
}
.projects-header h2 {
  margin: 0;
  font-size: 1.6rem;
  color: #0f172a;
}
.subtitle {
  margin: 6px 0 18px;
  color: #475569;
}

.projects-grid {
  display: grid;
  gap: 18px;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}

.project-card {
  background: white;
  border-radius: 12px;
  padding: 18px;
  box-shadow: 0 6px 18px rgba(2,6,23,0.06);
  border: 1px solid rgba(15,23,42,0.04);
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.project-image img {
  width: 100%;
  height: auto;
  border-radius: 12px;
  margin-bottom: 12px;
}

.card-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 12px;
}
.project-title {
  margin: 0;
  font-size: 1.05rem;
  color: #0f172a;
}
.project-sub {
  margin: 4px 0 0;
  color: #64748b;
  font-size: 0.9rem;
}
.tech {
  background: linear-gradient(90deg,#e6f0ff,#f0fcff);
  color: #0456b1;
  padding: 6px 10px;
  border-radius: 999px;
  font-size: 0.85rem;
  border: 1px solid rgba(4,86,177,0.08);
}

.desc {
  color: #334155;
  font-size: 0.95rem;
  margin: 0;
}

.card-actions {
  display: flex;
  gap: 10px;
  align-items: center;
}
.btn-outline, .btn-primary {
  padding: 8px 12px;
  border-radius: 8px;
  text-decoration: none;
  cursor: pointer;
  border: 1px solid transparent;
  font-weight: 600;
}
.btn-outline {
  background: transparent;
  color: #0f172a;
  border-color: rgba(15,23,42,0.06);
}
.btn-primary {
  background: #007bff;
  color: white;
  border-color: #007bff;
}
.btn-primary:hover { transform: translateY(-1px); }

.details {
  margin-top: 8px;
  padding-top: 8px;
  border-top: 1px dashed rgba(15,23,42,0.06);
  color: #334155;
}
.details h4 {
  margin: 8px 0 6px;
  color: #0f172a;
}
.details ul {
  margin: 0;
  padding-left: 18px;
}

.gallery-overlay {
  position: fixed;
  top:0; left:0;
  width:100%; height:100%;
  background: rgba(0,0,0,0.7);
  display:flex;
  justify-content:center;
  align-items:center;
  z-index:1000;
}
.gallery-content {
  position: relative;
  max-width: 90%;
  max-height: 90%;
}
.gallery-content img {
  max-width: 100%;
  max-height: 80vh;
  border-radius: 12px;
}
.close-btn {
  position:absolute;
  top:-10px; right:-10px;
  background:white;
  border:none;
  border-radius:50%;
  font-size: 18px;
  cursor:pointer;
  padding:4px 8px;
}
.gallery-nav {
  display:flex;
  justify-content:space-between;
  margin-top: 8px;
}
.gallery-nav button {
  background:#007bff;
  color:white;
  border:none;
  padding:6px 12px;
  border-radius:6px;
  cursor:pointer;
}
.gallery-nav button:disabled {
  background: #a0a0a0;
  cursor: not-allowed;
}

.fade-enter-active, .fade-leave-active {
  transition: all .18s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateY(-6px);
}
</style>
