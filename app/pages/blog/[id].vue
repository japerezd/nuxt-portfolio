<template>
  <div>
    <!-- We are inside the blog {{ $route.params.id }} -->
     We are inside the blog {{ route.params.id }}
  </div>
</template>

<script setup lang="ts">
const route = useRoute()

</script>