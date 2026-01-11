<script setup lang="ts">
import { watch } from 'vue';
import { X } from 'lucide-vue-next';

interface Props {
  isOpen: boolean;
  title?: string;
  size?: 'sm' | 'md' | 'lg' | 'xl';
}

const props = withDefaults(defineProps<Props>(), {
  size: 'md',
});

const emit = defineEmits<{
  close: [];
}>();

const sizes = {
  sm: 'max-w-md',
  md: 'max-w-lg',
  lg: 'max-w-2xl',
  xl: 'max-w-4xl',
};

watch(
  () => props.isOpen,
  (newValue) => {
    if (newValue) {
      document.body.style.overflow = 'hidden';
    } else {
      document.body.style.overflow = 'unset';
    }
  }
);

function handleClose() {
  emit('close');
}
</script>

<template>
  <Transition name="fade">
    <div v-if="isOpen">
      <div
        class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50"
        @click="handleClose"
      ></div>

      <div class="fixed inset-0 z-50 flex items-center justify-center p-4">
        <Transition name="scale">
          <div
            v-if="isOpen"
            :class="`relative bg-white dark:bg-gray-800 rounded-xl shadow-2xl w-full ${sizes[size]}`"
          >
            <div
              v-if="title"
              class="flex items-center justify-between px-6 py-4 border-b border-gray-200 dark:border-gray-700"
            >
              <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{ title }}</h3>
              <button
                @click="handleClose"
                class="text-gray-400 hover:text-gray-600 dark:hover:text-gray-300 transition-colors"
              >
                <X :size="20" />
              </button>
            </div>
            <button
              v-else
              @click="handleClose"
              class="absolute top-4 right-4 text-gray-400 hover:text-gray-600 dark:hover:text-gray-300 transition-colors z-10"
            >
              <X :size="20" />
            </button>

            <div class="px-6 py-4">
              <slot />
            </div>
          </div>
        </Transition>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.scale-enter-active,
.scale-leave-active {
  transition: all 0.2s;
}

.scale-enter-from,
.scale-leave-to {
  opacity: 0;
  transform: scale(0.95) translateY(20px);
}
</style>
