<script setup lang="ts">
import { computed } from 'vue';

interface Props {
  hover?: boolean;
  class?: string;
}

const props = withDefaults(defineProps<Props>(), {
  hover: false,
  class: '',
});

const baseStyles = 'bg-white dark:bg-gray-800 rounded-xl shadow-lg overflow-hidden';
const hoverStyles = props.hover
  ? 'transition-all duration-300 hover:shadow-2xl hover:-translate-y-1'
  : '';

const cardClasses = computed(() => {
  return `${baseStyles} ${hoverStyles} ${props.class}`;
});
</script>

<template>
  <div :class="cardClasses">
    <slot />
  </div>
</template>
