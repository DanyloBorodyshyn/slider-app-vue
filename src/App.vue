<script setup lang="ts">
import BaseSlider from './components/BaseSlider.vue'
import BaseForm from "./components/BaseForm.vue";
import BaseFilms from "./components/BaseFilms.vue";
</script>

<template>
  <div class="app">
    <section class="section-banner">
      <BaseSlider />
    </section>
    <section class="section-content">
      <BaseForm />
    </section>
    <section class="section-content">
      <BaseFilms />
    </section>
  </div>
</template>

<style lang="scss">
.app {
  padding-bottom: 60px;
}

.section-banner {
  margin-bottom: 40px;
}

.section-content {
  & + & {
    margin-top: 80px;
  }

  @media (max-width: 767px) {
    padding: 0 16px;
  }
}
</style>
