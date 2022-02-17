<script setup>
defineProps(["title"]);
defineEmits(["delete"]);
</script>

<template>
  <li>
    {{ title }}
    <button @click="$emit('delete')">Delete</button>
  </li>
</template>
