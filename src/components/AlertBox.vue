<script setup>
import { computed } from 'vue';
const { type } = defineProps(['type']);

const defaultContent = 'TODO:';
const defaultFooter = 'TODO:';
const defaultTitle = computed(() => {
  switch (type) {
    case 'WARNING':
      return 'Mild Warning';

    case 'ERROR':
    default:
      return 'Error';
  }
});
</script>

<template>
  <div
    class="alert-box"
    :class="{
      'border-red text-red': type === 'ERROR',
      'border-orange text-orange': type === 'WARNING',
    }"
  >
    <header class="title">
      <slot name="header">
        {{ defaultTitle }}
      </slot>
    </header>
    <main>
      <slot> {{ defaultContent }} </slot>
    </main>
    <footer>
      <slot name="footer">{{ defaultFooter }} </slot>
    </footer>
  </div>
</template>

<style scoped>
main {
  margin: 10px;
}

footer {
  font-size: small;
}

.alert-box {
  color: #666;
  border-radius: 4px;
  padding: 20px;
  background-color: #f8f8f8;
}

.title {
  font-weight: 600;
}

.border-orange {
  border: 1px solid orange;
}

.border-red {
  border: 1px solid red;
}

.text-red {
  color: red;
}

.text-orange {
  color: orange;
}
</style>
