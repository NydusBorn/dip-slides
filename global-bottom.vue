<script setup>

</script>

<template>
  <footer
      v-if="$nav.currentLayout !== 'cover'"
      class="absolute bottom-0 left-0 right-0 p-2"
  >
    {{ $nav.currentPage }} / {{ $nav.total }}
  </footer>
</template>

<style scoped>

</style>