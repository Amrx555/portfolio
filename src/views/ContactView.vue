<template>
  <div class="page">
    <span class="tag">Say Hello</span>
    <h2 class="sec-title">Get In <span class="accent">Touch</span></h2>

    <div class="contact-grid">
      <!-- Left: links -->
      <div class="c-items reveal">
        <a href="https://wa.me/201554681315" class="c-item">
          <div class="c-ico">
            <svg
              width="19"
              height="19"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                d="M20.52 3.48A11.94 11.94 0 0 0 12.06 0C5.5 0 .2 5.3.2 11.86c0 2.1.55 4.14 1.6 5.94L0 24l6.37-1.66a11.84 11.84 0 0 0 5.7 1.45c6.56 0 11.86-5.3 11.86-11.86 0-3.17-1.23-6.15-3.41-8.45z"
              />
              <path
                d="M16.2 13.9c-.27-.14-1.6-.8-1.85-.9-.25-.1-.43-.14-.61.14-.18.27-.7.9-.86 1.08-.16.18-.33.2-.6.07-.27-.14-1.14-.42-2.17-1.34-.8-.72-1.35-1.6-1.5-1.88-.16-.27-.02-.42.12-.56.12-.12.27-.33.4-.49.13-.16.18-.27.27-.45.09-.18.05-.33-.02-.47-.07-.14-.6-1.5-.83-2.07-.22-.55-.46-.47-.62-.48h-.53c-.18 0-.47.07-.72.33-.25.27-.94.92-.94 2.24s.96 2.6 1.1 2.79c.14.18 1.88 2.85 4.55 4 .63.27 1.13.44 1.52.57.64.2 1.22.18 1.67.11.51-.08 1.63-.66 1.86-1.3.22-.64.22-1.2.15-1.3-.06-.1-.25-.17-.52-.3z"
              />
            </svg>
          </div>
          <div>
            <div class="c-lbl">WhatsApp</div>
            <div class="c-val">01554681315</div>
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
