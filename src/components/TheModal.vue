<script setup lang="ts">
import TheButton from '@/components/TheButton.vue'

interface Props {
  isOpen: boolean
  title: string
}

const props = defineProps<Props>()

const emit = defineEmits(['close'])

</script>

<template>
  <div v-if="props.isOpen" class="modal">
    <TheButton class="btn btn-close" @click="emit('close')">

      <template #button-slot>

        <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M1 1L17 17M17 1L1 17" stroke="white" stroke-width="4" stroke-linecap="round" />
        </svg>

      </template>

    </TheButton>
    <h1>{{ props.title }}</h1>
  </div>
</template>

<style scoped lang="scss"></style>
