<script setup lang="ts">

const emit = defineEmits<{
  click: [value: boolean]
}>()

const btnOnClick = () => emit('click', true)

</script>

<template>
  <button class="btn" @click="btnOnClick">
    <slot name="button-slot"></slot>
  </button>
</template>

<style lang="scss" scoped></style>
