<!--
  Usage:

```md
---
layout: question-content
---

## Question Title

::content::
```js
// Code example
const answer = 42;
```

::options::
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
    class="slidev-layout question-content w-full h-full flex flex-col"
    :class="props.layoutClass"
  >
    <header :class="props.headerClass">
      <slot name="header" />
    </header>
    <footer :class="props.footerClass">
      <slot name="footer" />
    </footer>

    <div class="flex-1 flex flex-col px-12 py-8" :class="props.class">
      <div class="question-title">
        <slot />
      </div>

      <div class="flex-1 grid grid-cols-2 gap-8 mt-6">
        <div class="content-area flex items-center justify-center">
          <slot name="content" />
        </div>

        <div class="options-area flex items-center">
          <slot name="options" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-content :deep(.question-title h2) {
  margin-bottom: 0;
  text-align: center;
}

.question-content :deep(.content-area) {
  padding: 1.5rem;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 0.75rem;
  background: rgba(255, 255, 255, 0.05);
}

.question-content :deep(.content-area pre) {
  margin: 0;
  max-height: 100%;
  overflow: auto;
}

.question-content :deep(.content-area img) {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.question-content :deep(.options-area ul) {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  list-style: none;
  padding: 0;
  width: 100%;
  margin: 0;
}

.question-content :deep(.options-area li) {
  padding: 1rem 1.25rem;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 0.75rem;
  background: rgba(255, 255, 255, 0.05);
  transition: all 0.3s ease;
  cursor: pointer;
  font-size: 1rem;
  text-align: center;
}

.question-content :deep(.options-area li:hover) {
  border-color: rgba(255, 255, 255, 0.4);
  background: rgba(255, 255, 255, 0.1);
  transform: translateX(4px);
}

.question-content :deep(.options-area li code) {
  background: rgba(255, 255, 255, 0.1);
  padding: 0.2rem 0.4rem;
  border-radius: 0.25rem;
}
</style>
