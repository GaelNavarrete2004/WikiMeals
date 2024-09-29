<template>
  <a
    :href="href"
    target="_blank"
    class="px-3 py-2 rounded border-2 text-white border-[#FF0000] bg-[#FF0000] hover:bg-red-600 transition-colors"
  >
    <slot> Youtube </slot>
  </a>
</template>

<script setup>
const props = defineProps({
  href: String,
});
</script>
