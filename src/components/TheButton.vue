<script setup lang="ts"></script>

<template>
  <button class="btn" @click="$emit('click')">
    <slot name="button-slot"></slot>
  </button>
</template>

<style lang="scss" scoped></style>
