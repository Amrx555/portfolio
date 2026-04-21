<template>
  <div class="page">
    <div class="hero">
      <span class="home-eyebrow">
        <span class="dot-pulse"></span>
        Available for work
      </span>

      <h1 class="home-title">
        <span class="line accent">Amr Ibrahim</span>
        <span class="line sub-role">{{ txt }}<span class="blink"></span></span>
      </h1>

      <p class="home-sub">
        Junior Front-End Developer crafting clean, performant web experiences
        with Vue.js. Passionate about UI design and modern web technologies.
      </p>

      <div class="home-cta">
        <router-link to="/projects" class="btn-p">
          View Projects
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
        </router-link>
        <router-link to="/contact" class="btn-s">Get in Touch</router-link>
      </div>

      <div class="stats">
        <div class="stat">
          <div class="stat-n">7+</div>
          <div class="stat-l">Projects Built</div>
        </div>
        <div class="stat">
          <div class="stat-n">2+</div>
          <div class="stat-l">Years Learning</div>
        </div>
        <div class="stat">
          <div class="stat-n">Vue<em>3</em></div>
          <div class="stat-l">Main Framework</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const roles = [
  "Vue . js  Developer.",
  "UI Enthusiast.",
  "Problem Solver.",
  "Front-End Dev.",
];
const txt = ref("");
let ri = 0,
  ci = 0,
  del = false,
  t;

const go = () => {
  const cur = roles[ri];
  if (!del) {
    txt.value = cur.slice(0, ++ci);
    if (ci === cur.length) {
      del = true;
      t = setTimeout(go, 2200);
      return;
    }
  } else {
    txt.value = cur.slice(0, --ci);
    if (ci === 0) {
      del = false;
      ri = (ri + 1) % roles.length;
    }
  }
  t = setTimeout(go, del ? 55 : 110);
};

onMounted(() => {
  t = setTimeout(go, 900);
});
onUnmounted(() => clearTimeout(t));
</script>

<style scoped>
.hero {
  padding-top: 50px;
  display: flex;
  flex-direction: column;
  gap: 28px;
}

.home-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-size: 0.8rem;
  color: var(--green);
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  opacity: 0;
  animation: slideUp 0.6s 0.1s forwards;
}

.home-title {
  font-family: var(--display);
  font-size: clamp(3rem, 9vw, 6.5rem);
  font-weight: 800;
  line-height: 1.03;
  letter-spacing: -0.04em;
  opacity: 0;
  animation: slideUp 0.6s 0.25s forwards;
}
.home-title .line {
  display: block;
}
.home-title .accent {
  color: var(--green);
}
.home-title .sub-role {
  font-size: clamp(1.4rem, 3.5vw, 2.8rem);
  color: var(--muted);
  font-weight: 600;
}

.blink {
  display: inline-block;
  width: 3px;
  height: 0.85em;
  background: var(--green);
  margin-left: 3px;
  vertical-align: middle;
  animation: blink 1s step-end infinite;
}
@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}

.home-sub {
  font-size: 1.05rem;
  color: var(--muted);
  max-width: 480px;
  line-height: 1.75;
  opacity: 0;
  animation: slideUp 0.6s 0.4s forwards;
}

.home-cta {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  opacity: 0;
  animation: slideUp 0.6s 0.55s forwards;
}

.stats {
  display: flex;
  gap: 40px;
  flex-wrap: wrap;
  opacity: 0;
  animation: slideUp 0.6s 0.7s forwards;
  padding-top: 8px;
}
.stat-n {
  font-family: var(--display);
  font-size: 2rem;
  font-weight: 800;
  color: var(--green);
  line-height: 1;
}
.stat-n em {
  color: var(--green);
  font-style: normal;
}
.stat-l {
  font-size: 0.72rem;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-top: 4px;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(26px);
  }
  to {
    opacity: 1;
    transform: none;
  }
}

@media (max-width: 480px) {
  .stats {
    gap: 28px;
  }
}
</style>
