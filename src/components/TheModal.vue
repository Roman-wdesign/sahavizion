<script setup lang="ts">
import TheButton from '@/components/TheButton.vue'
import { ref } from 'vue'

interface Props {
  isOpen: boolean
  title: string
}

const props = defineProps<Props>()
const emit = defineEmits(['close'])


const expandedFolders = ref(new Set());

const mockFolders = [
  {
    id: 1,
    name: 'Папка 1',
    children: [
      { id: 2, name: 'Папка 1.1', children: [] },
      {
        id: 3,
        name: 'Папка 1.2',
        children: [{ id: 4, name: 'Папка 1.2.1', children: [] }],
      },
    ],
  },
  { id: 5, name: 'Папка 2', children: [] },
];


const toggleFolder = (id: number) => {
  if (expandedFolders.value.has(id)) {
    expandedFolders.value.delete(id);
  } else {
    expandedFolders.value.add(id);
  }
};
</script>

<template>
  <div v-if="props.isOpen" class="modal">

    <!-- Close button -->
    <TheButton class="btn btn-close" @click="emit('close')">

      <template #button-slot>

        <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M1 1L17 17M17 1L1 17" stroke="white" stroke-width="4" stroke-linecap="round" />
        </svg>

      </template>

    </TheButton>

    <!-- Title -->
    <h1 class="modal__title">{{ props.title }}</h1>

    <!-- Render list -->
    <ul class="list">
      <li class="list__item" v-for="folder in mockFolders" :key="folder.id">
        <span class="list__item-sign" @click="toggleFolder(folder.id)">
          {{ expandedFolders.has(folder.id) ? '-' : '+' }}
        </span>
        {{ folder.name }}
        <ul v-if="expandedFolders.has(folder.id)">
          <li v-for="child in folder.children" :key="child.id">
            {{ child.name }}
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss"></style>
