<script setup lang="ts">
import TheButton from '@/components/TheButton.vue'
import { ref, watch } from 'vue'

interface Props {
  isOpen: boolean
  title: string
}

interface Folder {
  id: number
  name: string
  children: Folder[]
}

const props = defineProps<Props>()

const expandedFolders = ref<Set<number>>(new Set())
const selectedFolderId = ref<number | null>(null)

const emit = defineEmits<{
  (event: 'update:isOpen', value: boolean): void
}>()

const mockFolders: Folder[] = [
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
]

const oModal = ref(props.isOpen)

watch(
  () => props.isOpen,
  (newValue) => {
    oModal.value = newValue
  }
)

const toggleFolder = (id: number): void => {
  if (expandedFolders.value.has(id)) {
    expandedFolders.value.delete(id)
  } else {
    expandedFolders.value.add(id)
  }
}

const selectFolder = (id: number): void => {
  selectedFolderId.value = id
}

const confirmSelection = (): void => {
  console.log('Выбрана папка с ID:', selectedFolderId.value)
  justCloseIt()
}

const justCloseIt = (): void => {
  oModal.value = false
  emit('update:isOpen', false) // Эмитим событие для синхронизации с основным компонентом
}
</script>

<template>
  <div v-if="oModal" class="modal">
    <TheButton class="btn btn-close" @click="justCloseIt">
      <template #button-slot>
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M1 1L17 17M17 1L1 17" stroke="white" stroke-width="4" stroke-linecap="round" />
        </svg>
      </template>
    </TheButton>

    <h1 class="modal__title">{{ props.title }}</h1>

    <ul class="list">
      <li class="list__item" v-for="folder in mockFolders" :key="folder.id">
        <span class="list__item-sign" @click="toggleFolder(folder.id)">
          {{ expandedFolders.has(folder.id) ? '-' : '+' }}
        </span>
        <span @click="selectFolder(folder.id)" :class="{ 'strong-style': selectedFolderId === folder.id }">
          {{ folder.name }}</span>
        <ul v-if="expandedFolders.has(folder.id)" class="list__sub">
          <li v-for="child in folder.children" :key="child.id" class="list__item">
            <span class="list__item-sign" @click="toggleFolder(child.id)">
              {{ expandedFolders.has(child.id) ? '-' : '+' }}
            </span>
            <span :class="{ 'strong-style': selectedFolderId === child.id }" @click="selectFolder(child.id)">
              {{ child.name }}
            </span>
          </li>
        </ul>
      </li>
    </ul>
    <TheButton class="btn btn-ok" @click="confirmSelection">
      <template #button-slot>Ok</template>
    </TheButton>
  </div>
</template>

<style scoped lang="scss"></style>
