<template>
  <div class="page">
    <span class="tag">Say Hello</span>
    <h2 class="sec-title">Get In <span class="accent">Touch</span></h2>

    <div class="contact-grid">
      <!-- Left: links -->
      <div class="c-items reveal">
        <a href="mailto:amri69217@gmail.com" class="c-item">
          <div class="c-ico">
            <svg
              width="19"
              height="19"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              viewBox="0 0 24 24"
            >
              <rect x="2" y="4" width="20" height="16" rx="2" />
              <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
            </svg>
          </div>
          <div>
            <div class="c-lbl">Email</div>
            <div class="c-val">amri69217@gmail.com</div>
          </div>
        </a>

        <a href="https://github.com/amrx555" target="_blank" class="c-item">
          <div class="c-ico">
            <svg width="19" height="19" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M12 2C6.48 2 2 6.48 2 12c0 4.42 2.87 8.17 6.84 9.49.5.09.68-.22.68-.48v-1.69c-2.78.6-3.37-1.34-3.37-1.34-.45-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.61.07-.61 1 .07 1.53 1.03 1.53 1.03.89 1.52 2.34 1.08 2.91.83.09-.65.35-1.08.63-1.33-2.22-.25-4.55-1.11-4.55-4.94 0-1.09.39-1.98 1.03-2.68-.1-.26-.45-1.27.1-2.64 0 0 .84-.27 2.75 1.02A9.56 9.56 0 0 1 12 6.8c.85.004 1.71.115 2.51.337 1.91-1.29 2.75-1.02 2.75-1.02.55 1.37.2 2.38.1 2.64.64.7 1.03 1.59 1.03 2.68 0 3.84-2.34 4.69-4.57 4.93.36.31.68.92.68 1.85v2.74c0 .27.18.58.69.48A10.01 10.01 0 0 0 22 12c0-5.52-4.48-10-10-10z"
              />
            </svg>
          </div>
          <div>
            <div class="c-lbl">GitHub</div>
            <div class="c-val">github.com/amrx555</div>
          </div>
        </a>

        <a
          href="https://linkedin.com/in/amr-ibrahem-44545131a"
          target="_blank"
          class="c-item"
        >
          <div class="c-ico">
            <svg width="19" height="19" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"
              />
              <circle cx="4" cy="4" r="2" />
            </svg>
          </div>
          <div>
            <div class="c-lbl">LinkedIn</div>
            <div class="c-val">Amr Ibrahem</div>
          </div>
        </a>
      </div>

      <!-- Right: CTA -->
      <div class="contact-right reveal" style="transition-delay: 0.15s">
        <div class="status-badge">
          <span class="dot-pulse"></span>
          Open to opportunities
        </div>
        <p class="cta-head">
          Let's build something
          <span class="accent">great</span> together.
        </p>
        <p class="cta-sub">
          I'm currently open to junior positions and freelance projects. Whether
          you have a project in mind or just want to connect â€” my inbox is
          always open.
        </p>
        <a href="mailto:amri69217@gmail.com" class="btn-p">
          Send Email
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
  </div>
</template>

<script setup>
import { onMounted, nextTick } from "vue";

onMounted(() => {
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
});
</script>

<style scoped>
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  margin-top: 60px;
}

.c-items {
  display: flex;
  flex-direction: column;
  gap: 18px;
}
.c-item {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 18px 22px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 16px;
  text-decoration: none;
  color: var(--text);
  transition: all 0.28s;
}
.c-item:hover {
  border-color: rgba(66, 184, 131, 0.4);
  transform: translateX(5px);
  background: var(--surface-hover);
}

.c-ico {
  width: 42px;
  height: 42px;
  background: var(--green-dim);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--green);
  flex-shrink: 0;
}
.c-lbl {
  font-size: 0.72rem;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 3px;
}
.c-val {
  font-size: 0.925rem;
  font-weight: 500;
}

.contact-right {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 20px;
}

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 9px;
  padding: 10px 18px;
  background: var(--green-dim);
  border: 1px solid rgba(66, 184, 131, 0.25);
  border-radius: 100px;
  font-size: 0.82rem;
  color: var(--green);
  font-weight: 500;
  align-self: flex-start;
}

.cta-head {
  font-family: var(--display);
  font-size: clamp(1.6rem, 3.5vw, 2.4rem);
  font-weight: 800;
  line-height: 1.18;
  letter-spacing: -0.035em;
}
.cta-head .accent {
  color: var(--green);
}

.cta-sub {
  font-size: 0.975rem;
  color: var(--muted);
  line-height: 1.78;
}

@media (max-width: 768px) {
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 44px;
  }
}
</style>
