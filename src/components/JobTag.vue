<template>
  <button
    @click="$emit('tag', text)"
    class="bg-teal-100 p-2 text-xs text-teal-600 hover:bg-teal-600 hover:text-white transition duration-500 rounded-md font-bold"
  >{{ text }}</button>
</template>

<script>
export default {
  props: ['text'],
  methods: {
  }
}
</script>

<style>
</style>