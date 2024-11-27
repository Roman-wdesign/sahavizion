<script setup lang="ts">
import { ref } from 'vue'

import TheModal from '@/components/TheModal.vue'
import TheButton from '@/components/TheButton.vue'

const openModal = ref(false)
</script>

<template>
  <div>
    <section class="section-one">
      <div class="div-block"></div>
      <TheModal :title="'Модальное окно'" :isOpen="openModal" @close="openModal = false"></TheModal>
      <TheButton class="btn main-btn" @click="openModal = true">
        <template #button-slot>открыть</template>
      </TheButton>
    </section>
  </div>
</template>

<style scoped lang="scss"></style>
