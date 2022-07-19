<script setup lang="ts">
defineProps<{stone: number}>()
</script>

<template>
    <span v-if="stone === 1" >●</span>
    <span v-if="stone === -1" >○</span>
    <span v-if="stone === 0" >&nbsp;</span>
</template>