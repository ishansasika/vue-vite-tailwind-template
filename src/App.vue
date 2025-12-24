<script setup lang="ts">
import { RouterView } from 'vue-router'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
</script>

<template>
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
