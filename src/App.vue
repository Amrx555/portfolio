<template>
  <div>
    <!-- Background -->
    <div class="bg-canvas">
      <div class="orb orb-1"></div>
      <div class="orb orb-2"></div>
      <div class="orb orb-3"></div>
    </div>
    <div class="grain"></div>

    <!-- Scroll progress -->
    <div class="scroll-bar" ref="spb"></div>

    <!-- Nav -->
    <nav>
      <router-link to="/" class="logo">amr<em>.</em></router-link>
      <ul class="nav-links">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/projects">Projects</router-link></li>
        <li><router-link to="/about">About</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
      <div class="burger" :class="{ open: mob }" @click="mob = !mob">
        <span></span><span></span><span></span>
      </div>
    </nav>

    <!-- Mobile Menu -->
    <div class="m-menu" :class="{ open: mob }">
      <router-link to="/" @click="mob = false">Home</router-link>
      <router-link to="/projects" @click="mob = false">Projects</router-link>
      <router-link to="/about" @click="mob = false">About</router-link>
      <router-link to="/contact" @click="mob = false">Contact</router-link>
    </div>

    <!-- Router -->
    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const mob = ref(false);
const spb = ref(null);

onMounted(() => {
  window.addEventListener("scroll", () => {
    const p =
      (window.scrollY / (document.body.scrollHeight - window.innerHeight)) *
      100;
    spb.value.style.width = Math.min(p, 100) + "%";
  });
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap");

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --bg: #06060f;
  --surface: rgba(255, 255, 255, 0.04);
  --surface-hover: rgba(255, 255, 255, 0.07);
  --border: rgba(255, 255, 255, 0.07);
  --green: #42b883;
  --green-dim: rgba(66, 184, 131, 0.15);
  --green-glow: rgba(66, 184, 131, 0.35);
  --mint: #64ffda;
  --text: #e2e8f0;
  --muted: #8892b0;
  --display: "Syne", sans-serif;
  --body: "DM Sans", sans-serif;
}

html {
  scroll-behavior: smooth;
}

body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--body);
  min-height: 100vh;
  overflow-x: hidden;
  cursor: default;
}

/* â”€â”€ BACKGROUND â”€â”€ */
.bg-canvas {
  position: fixed;
  inset: 0;
  z-index: 0;
  overflow: hidden;
}
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(110px);
  animation: drift 22s ease-in-out infinite;
}
.orb-1 {
  width: 650px;
  height: 650px;
  background: radial-gradient(circle, #42b883, transparent 70%);
  top: -220px;
  left: -180px;
  opacity: 0.12;
  animation-delay: 0s;
}
.orb-2 {
  width: 420px;
  height: 420px;
  background: radial-gradient(circle, #35495e, transparent 70%);
  bottom: -120px;
  right: -100px;
  opacity: 0.14;
  animation-delay: -8s;
}
.orb-3 {
  width: 280px;
  height: 280px;
  background: radial-gradient(circle, #64ffda, transparent 70%);
  top: 45%;
  left: 60%;
  opacity: 0.08;
  animation-delay: -15s;
}

@keyframes drift {
  0%,
  100% {
    transform: translate(0, 0) scale(1);
  }
  33% {
    transform: translate(28px, -24px) scale(1.04);
  }
  66% {
    transform: translate(-18px, 22px) scale(0.96);
  }
}

.grain {
  position: fixed;
  inset: -200%;
  width: 400%;
  height: 400%;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  opacity: 0.022;
  pointer-events: none;
  z-index: 1;
  animation: grainAnim 7s steps(10) infinite;
}
@keyframes grainAnim {
  0% {
    transform: translate(0, 0);
  }
  10% {
    transform: translate(-5%, -10%);
  }
  20% {
    transform: translate(-15%, 5%);
  }
  30% {
    transform: translate(7%, -25%);
  }
  40% {
    transform: translate(-5%, 25%);
  }
  50% {
    transform: translate(-15%, 10%);
  }
  60% {
    transform: translate(15%, 0);
  }
  70% {
    transform: translate(0, 15%);
  }
  80% {
    transform: translate(3%, 35%);
  }
  90% {
    transform: translate(-10%, 10%);
  }
  100% {
    transform: translate(0, 0);
  }
}

/* â”€â”€ SCROLL BAR â”€â”€ */
.scroll-bar {
  position: fixed;
  top: 0;
  left: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--green), var(--mint));
  z-index: 200;
  transition: width 0.08s linear;
  width: 0;
}

/* â”€â”€ NAV â”€â”€ */
nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 18px 48px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  background: rgba(6, 6, 15, 0.72);
  border-bottom: 1px solid var(--border);
}

.logo {
  font-family: var(--display);
  font-size: 1.35rem;
  font-weight: 800;
  color: var(--text);
  text-decoration: none;
  letter-spacing: -0.03em;
}
.logo em {
  color: var(--green);
  font-style: normal;
}

.nav-links {
  display: flex;
  gap: 4px;
  list-style: none;
}
.nav-links a {
  color: var(--muted);
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 500;
  padding: 8px 18px;
  border-radius: 10px;
  transition: all 0.2s;
  position: relative;
}
.nav-links a:hover,
.nav-links a.router-link-active {
  color: var(--text);
  background: var(--surface);
}
.nav-links a.router-link-active::after {
  content: "";
  position: absolute;
  bottom: 5px;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 4px;
  background: var(--green);
  border-radius: 50%;
}

/* hamburger */
.burger {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
  padding: 4px;
  z-index: 101;
}
.burger span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--text);
  border-radius: 2px;
  transition: all 0.3s;
}
.burger.open span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}
.burger.open span:nth-child(2) {
  opacity: 0;
  transform: translateX(-8px);
}
.burger.open span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* mobile menu */
.m-menu {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(6, 6, 15, 0.97);
  z-index: 99;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 28px;
  backdrop-filter: blur(30px);
}
.m-menu.open {
  display: flex;
}
.m-menu a {
  font-family: var(--display);
  font-size: 2.4rem;
  font-weight: 800;
  color: var(--text);
  text-decoration: none;
  letter-spacing: -0.04em;
  transition: color 0.2s;
  opacity: 0;
  animation: menuIn 0.4s forwards;
}
.m-menu a:hover {
  color: var(--green);
}
.m-menu a:nth-child(1) {
  animation-delay: 0.05s;
}
.m-menu a:nth-child(2) {
  animation-delay: 0.1s;
}
.m-menu a:nth-child(3) {
  animation-delay: 0.15s;
}
.m-menu a:nth-child(4) {
  animation-delay: 0.2s;
}
@keyframes menuIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: none;
  }
}

/* â”€â”€ PAGE TRANSITION â”€â”€ */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.35s, transform 0.35s;
}
.fade-enter-from {
  opacity: 0;
  transform: translateY(18px);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

/* â”€â”€ SHARED â”€â”€ */
.page {
  position: relative;
  z-index: 2;
  min-height: 100vh;
  padding: 130px 48px 90px;
  max-width: 1080px;
  margin: 0 auto;
}

.tag {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 0.78rem;
  color: var(--green);
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  margin-bottom: 14px;
}
.tag::before {
  content: "";
  width: 22px;
  height: 1px;
  background: var(--green);
}

.sec-title {
  font-family: var(--display);
  font-size: clamp(2rem, 5vw, 3.6rem);
  font-weight: 800;
  line-height: 1.08;
  letter-spacing: -0.035em;
  margin-bottom: 24px;
}
.sec-title .accent {
  color: var(--green);
}

.btn-p {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 13px 26px;
  background: var(--green);
  color: #000;
  font-weight: 700;
  font-size: 0.9rem;
  border-radius: 12px;
  text-decoration: none;
  transition: all 0.25s;
  border: none;
  cursor: none;
}
.btn-p:hover {
  background: var(--mint);
  transform: translateY(-2px);
  box-shadow: 0 14px 40px var(--green-glow);
}

.btn-s {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 13px 26px;
  background: var(--surface);
  color: var(--text);
  font-weight: 500;
  font-size: 0.9rem;
  border-radius: 12px;
  text-decoration: none;
  border: 1px solid var(--border);
  transition: all 0.25s;
}
.btn-s:hover {
  border-color: var(--green);
  background: var(--surface-hover);
  transform: translateY(-2px);
}

.dot-pulse {
  width: 7px;
  height: 7px;
  background: var(--green);
  border-radius: 50%;
  animation: pulse 2s infinite;
  display: inline-block;
}
@keyframes pulse {
  0%,
  100% {
    box-shadow: 0 0 0 0 var(--green-glow);
  }
  70% {
    box-shadow: 0 0 0 8px transparent;
  }
}

.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.7s cubic-bezier(0.4, 0, 0.2, 1),
    transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}
.reveal.visible {
  opacity: 1;
  transform: none;
}

/* â”€â”€ RESPONSIVE â”€â”€ */
@media (max-width: 768px) {
  nav {
    padding: 15px 20px;
  }
  .nav-links {
    display: none;
  }
  .burger {
    display: flex;
  }
  .page {
    padding: 100px 22px 70px;
  }
}
</style>
