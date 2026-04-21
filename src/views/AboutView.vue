<template>
  <div class="page">
    <span class="tag">Who I am</span>
    <h2 class="sec-title">About <span class="accent">Me</span></h2>

    <div class="about-grid">
      <!-- Left: text + chips -->
      <div class="reveal">
        <div class="about-text">
          <p>
            I'm <strong>Amr Ibrahim</strong>, a Junior Front-End Developer
            passionate about building responsive, visually engaging web
            experiences.
          </p>
          <p>
            I focus on <strong>clean UI design</strong> and writing maintainable
            code. I love turning ideas into interactive, pixel-perfect
            interfaces that users actually enjoy.
          </p>
          <p>
            Currently deepening my expertise in <strong>Vue.js</strong>,
            component architecture, and modern CSS â€” always learning, always
            shipping.
          </p>
        </div>
        <div class="chips">
          <span class="chip" v-for="t in techs" :key="t">{{ t }}</span>
        </div>
      </div>

      <!-- Right: skill bars -->
      <div class="skills reveal" style="transition-delay: 0.12s">
        <div class="skill-item" v-for="s in skills" :key="s.name">
          <div class="sk-head">
            <span>{{ s.name }}</span>
            <span class="sk-pct">{{ s.pct }}%</span>
          </div>
          <div class="sk-track">
            <div
              class="sk-fill"
              :class="{ on: s.animated }"
              :style="{ '--w': s.pct + '%' }"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from "vue";

const techs = [
  "HTML5",
  "CSS3",
  "JavaScript",
  "Vue.js",
  "Bootstrap",
  "Git",
  "Responsive Design",
  "Figma",
  "Tailwind CSS",
];

const skills = ref([
  { name: "HTML & CSS", pct: 90, animated: false },
  { name: "JavaScript", pct: 75, animated: false },
  { name: "Vue.js", pct: 80, animated: false },
  { name: "Bootstrap", pct: 85, animated: false },
  { name: "Tailwind CSS", pct: 95, animated: false },
  { name: "Git & GitHub", pct: 70, animated: false },
]);

onMounted(() => {
  /* Reveal on scroll */
  nextTick(() => {
    const io = new IntersectionObserver(
      (entries) => {
        entries.forEach((e) => {
          if (e.isIntersecting) {
            e.target.classList.add("visible");
            io.unobserve(e.target);
          }
        });
      },
      { threshold: 0.15 }
    );
    document.querySelectorAll(".reveal").forEach((el) => io.observe(el));
  });

  /* Skill bars */
  setTimeout(() => {
    skills.value.forEach((s, i) =>
      setTimeout(() => {
        s.animated = true;
      }, i * 160)
    );
  }, 400);
});
</script>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  margin-top: 60px;
  align-items: start;
}

.about-text {
  font-size: 1rem;
  color: var(--muted);
  line-height: 1.82;
}
.about-text p {
  margin-bottom: 16px;
}
.about-text strong {
  color: var(--text);
  font-weight: 500;
}

.chips {
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
  margin-top: 36px;
}
.chip {
  padding: 7px 15px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 100px;
  font-size: 0.82rem;
  color: var(--muted);
  transition: all 0.2s;
  cursor: default;
}
.chip:hover {
  border-color: var(--green);
  color: var(--text);
  background: var(--green-dim);
}

.skills {
  display: flex;
  flex-direction: column;
  gap: 22px;
}

.sk-head {
  display: flex;
  justify-content: space-between;
  margin-bottom: 9px;
  font-size: 0.875rem;
  font-weight: 500;
}
.sk-pct {
  color: var(--green);
  font-weight: 600;
}
.sk-track {
  height: 3px;
  background: var(--border);
  border-radius: 3px;
  overflow: hidden;
}
.sk-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--green), var(--mint));
  border-radius: 3px;
  width: 0;
  transition: width 1.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.sk-fill.on {
  width: var(--w);
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 44px;
  }
}
</style>
