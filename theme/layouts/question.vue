<!--
  Usage:

```md
---
layout: question
---

## Question Title

- Option A
- Option B
- Option C
- Option D
```

-->

<script setup lang="ts">
const props = defineProps({
  class: {
    type: String,
  },
  layoutClass: {
    type: String,
  },
  headerClass: {
    type: String,
  },
  footerClass: {
    type: String,
  },
});
</script>

<template>
  <div
    class="slidev-layout question w-full h-full flex flex-col"
    :class="props.layoutClass"
  >
    <header :class="props.headerClass">
      <slot name="header" />
    </header>
    <footer :class="props.footerClass">
      <slot name="footer" />
    </footer>

    <div
      class="flex-1 flex flex-col justify-center items-center px-12"
      :class="props.class"
    >
      <slot />
    </div>
  </div>
</template>

<style scoped>
.question :deep(h2) {
  margin-bottom: 2rem;
  text-align: center;
}

.question :deep(ul) {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  list-style: none;
  padding: 0;
  width: 100%;
  max-width: 1000px;
}

.question :deep(li) {
  padding: 1.25rem 1.5rem;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 0.75rem;
  background: rgba(255, 255, 255, 0.05);
  transition: all 0.3s ease;
  cursor: pointer;
  font-size: 1.1rem;
  text-align: center;
}

.question :deep(li:hover) {
  border-color: rgba(255, 255, 255, 0.4);
  background: rgba(255, 255, 255, 0.1);
  transform: translateY(-2px);
}

.question :deep(li code) {
  background: rgba(255, 255, 255, 0.1);
  padding: 0.2rem 0.4rem;
  border-radius: 0.25rem;
}
</style>
