<script setup lang="ts">
import { useRouter } from 'vue-router';
import { Home, ArrowLeft } from 'lucide-vue-next';
import Button from '../components/ui/Button.vue';

const router = useRouter();

function goBack() {
  router.back();
}
</script>

<template>
  <div
    class="min-h-screen bg-gradient-to-br from-blue-50 via-white to-purple-50 dark:from-gray-900 dark:via-gray-800 dark:to-gray-900 flex items-center justify-center px-4"
  >
    <div class="max-w-2xl w-full text-center">
      <Transition name="fade" appear>
        <div>
          <h1
            class="text-9xl font-bold bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent mb-4 animate-scale-in"
          >
            404
          </h1>

          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mb-4">
            Page Not Found
          </h2>

          <p class="text-lg text-gray-600 dark:text-gray-400 mb-8">
            Oops! The page you're looking for doesn't exist. It might have been moved or deleted.
          </p>

          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <RouterLink to="/">
              <Button size="lg">
                <Home class="mr-2" :size="20" />
                Go Home
              </Button>
            </RouterLink>
            <Button variant="outline" size="lg" @click="goBack">
              <ArrowLeft class="mr-2" :size="20" />
              Go Back
            </Button>
          </div>

          <div class="mt-16">
            <svg
              class="w-full max-w-md mx-auto"
              viewBox="0 0 400 300"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="200" cy="150" r="100" class="fill-blue-100 dark:fill-blue-900/20" />
              <path
                d="M150 120 L170 140 L150 160"
                class="stroke-blue-600 dark:stroke-blue-400"
                stroke-width="8"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M250 120 L230 140 L250 160"
                class="stroke-purple-600 dark:stroke-purple-400"
                stroke-width="8"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>
        </div>
      </Transition>
    </div>
  </div>
</template>

<style scoped>
@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes scale-in {
  from {
    transform: scale(0.5);
  }
  to {
    transform: scale(1);
  }
}

.fade-enter-active {
  animation: fade-in 0.5s ease-out;
}

.animate-scale-in {
  animation: scale-in 0.5s cubic-bezier(0.34, 1.56, 0.64, 1) 0.2s both;
}
</style>
