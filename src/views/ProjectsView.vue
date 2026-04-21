<template>
  <div class="page">
    <span class="tag">My Work</span>
    <h2 class="sec-title">Featured <span class="accent">Projects</span></h2>

    <!-- Filters -->
    <div class="filter-row">
      <button
        class="f-btn"
        :class="{ on: filter === 'all' }"
        @click="filter = 'all'"
      >
        All ({{ projects.length }})
      </button>
      <button
        class="f-btn"
        :class="{ on: filter === 'js' }"
        @click="filter = 'js'"
      >
        JavaScript ({{ projects.filter((p) => p.type === "js").length }})
      </button>
      <button
        class="f-btn"
        :class="{ on: filter === 'vue' }"
        @click="filter = 'vue'"
      >
        Vue.js ({{ projects.filter((p) => p.type === "vue").length }})
      </button>
    </div>

    <!-- Empty state -->
    <div v-if="filteredProjects.length === 0" class="empty-state">
      <span>ðŸš§</span>
      <p>
        No {{ filter === "vue" ? "Vue.js" : "JavaScript" }} projects yet â€”
        coming soon!
      </p>
    </div>

    <!-- Grid -->
    <div class="proj-grid" v-else>
      <div
        class="p-card"
        v-for="(p, i) in filteredProjects"
        :key="p.id"
        :style="{ animationDelay: i * 0.1 + 's' }"
      >
        <div class="card-top">
          <div class="c-num">{{ String(i + 1).padStart(2, "0") }}</div>
          <div class="c-badge">
            {{ p.type === "js" ? "JavaScript" : "Vue.js" }}
          </div>
        </div>

        <h3 class="c-title">{{ p.title }}</h3>
        <p class="c-desc">{{ p.desc }}</p>

        <a
          :href="p.link"
          target="_blank"
          rel="noopener noreferrer"
          class="c-link"
        >
          View Project
          <svg
            width="15"
            height="15"
            fill="none"
            stroke="currentColor"
            stroke-width="2.5"
            viewBox="0 0 24 24"
          >
            <path d="M5 12h14M12 5l7 7-7 7" />
          </svg>
        </a>
      </div>
    </div>

    <!-- CV -->
    <div class="cv-wrap">
      <a
        v-if="cvReady"
        href="/cv.pdf"
        download="Amr_Ibrahim_CV.pdf"
        class="btn-p"
      >
        Download CV
        <svg
          width="15"
          height="15"
          fill="none"
          stroke="currentColor"
          stroke-width="2.5"
          viewBox="0 0 24 24"
        >
          <path d="M12 16l-4-4h3V4h2v8h3l-4 4z" />
          <path d="M4 20h16" />
        </svg>
      </a>
      <div v-else class="cv-note">CV will be available soon!</div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const filter = ref("all");
const cvReady = ref(false);

const projects = [
  {
    id: 1,
    title: "Gym Website",
    desc: "Responsive fitness website built with Bootstrap. Features smooth scrolling, mobile-first design, and modern section layouts.",
    link: "https://sage-malabi-4cf839.netlify.app/",
    type: "vue",
  },
  {
    id: 2,
    title: "Notes App",
    desc: "Clean note-taking app built with Vue.js. Supports adding, editing, and deleting notes with local storage persistence.",
    link: "https://whimsical-kataifi-9a5843.netlify.app/",
    type: "vue",
  },
  {
    id: 3,
    title: "booknest",
    desc: "A Vue.js-based book management application where users can discover books, organize their collection, and enjoy a fast, dynamic user experience.",
    link: "https://effortless-pegasus-c86822.netlify.app/",
    type: "vue",
  },
  {
    id: 4,
    title: "Mini E-commerce",
    desc: "JavaScript shopping site with product listings, cart functionality, and a smooth checkout flow â€” no frameworks.",
    link: "https://amrx555.github.io/Mini-E-commerce/",
    type: "js",
  },
  {
    id: 5,
    title: "Inventory System",
    desc: "JavaScript inventory management system to track products, quantities, and categories through an intuitive dashboard.",
    link: "https://amrx555.github.io/Booking-System/",
    type: "js",
  },
  {
    id: 6,
    title: "Admin Dashboard",
    desc: "Fully responsive admin panel built in vanilla JavaScript, featuring data tables, stats cards, and a sidebar layout.",
    link: "https://amrx555.github.io/Admin-Dashboard/",
    type: "js",
  },
];
const filteredProjects = computed(() =>
  filter.value === "all"
    ? projects
    : projects.filter((p) => p.type === filter.value)
);
</script>

<style scoped>
.filter-row {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
  margin: 36px 0;
}
.f-btn {
  padding: 8px 20px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 100px;
  color: var(--muted);
  font-size: 0.845rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
  font-family: var(--body);
}
.f-btn:hover {
  background: var(--surface-hover);
  color: var(--text);
}
.f-btn.on {
  background: var(--green);
  border-color: var(--green);
  color: #000;
  font-weight: 700;
}

.empty-state {
  text-align: center;
  padding: 80px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
}
.empty-state span {
  font-size: 3rem;
}
.empty-state p {
  color: var(--muted);
  font-size: 1rem;
}

.proj-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 22px;
}

.p-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 28px;
  transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
  position: relative;
  overflow: hidden;
  animation: cardIn 0.5s both;
}
@keyframes cardIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: none;
  }
}
.p-card::before {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(66, 184, 131, 0.07),
    transparent 60%
  );
  opacity: 0;
  transition: opacity 0.3s;
  pointer-events: none;
}
.p-card:hover {
  border-color: rgba(66, 184, 131, 0.4);
  transform: translateY(-6px);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3), 0 0 0 1px rgba(66, 184, 131, 0.08);
}
.p-card:hover::before {
  opacity: 1;
}

.card-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}
.c-num {
  font-family: var(--display);
  font-size: 0.72rem;
  font-weight: 700;
  color: var(--green);
  letter-spacing: 0.16em;
}
.c-badge {
  padding: 3px 10px;
  background: rgba(66, 184, 131, 0.12);
  color: var(--green);
  border-radius: 6px;
  font-size: 0.72rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}
.c-title {
  font-family: var(--display);
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 10px;
  letter-spacing: -0.02em;
}
.c-desc {
  font-size: 0.875rem;
  color: var(--muted);
  line-height: 1.65;
  margin-bottom: 24px;
}

.c-link {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  padding: 9px 18px;
  background: var(--surface-hover);
  border: 1px solid var(--border);
  border-radius: 10px;
  color: var(--text);
  font-size: 0.845rem;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.22s;
}
.c-link:hover {
  background: var(--green);
  border-color: var(--green);
  color: #000;
}
.c-link .arrow {
  transition: transform 0.2s;
}
.c-link:hover .arrow {
  transform: translate(2px, -2px);
}

.cv-wrap {
  text-align: center;
  margin-top: 60px;
}
.cv-note {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 22px;
  background: rgba(66, 184, 131, 0.08);
  border: 1px dashed rgba(66, 184, 131, 0.3);
  border-radius: 12px;
  color: var(--muted);
  font-size: 0.875rem;
}

@media (max-width: 480px) {
  .proj-grid {
    grid-template-columns: 1fr;
  }
}
</style>
