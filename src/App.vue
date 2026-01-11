<script setup lang="ts">
import { RouterView } from 'vue-router';
import { Toaster } from 'vue-sonner';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <Toaster position="top-right" :duration="3000" />
  <div class="page-container">
    <Header />
    <div class="content-wrapper">
      <RouterView />
    </div>
    <Footer />
  </div>
</template>

<style>
@import './App.css';
</style>
