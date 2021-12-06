<template>
  <div class="flex items-center h-14 justify-between px-8 py-4 bg-white rounded-md shadow-xl mt-32 mb-9">
    <div class="h-full  flex items-center space-x-4">
      <FilterTag v-for="tag in tags" :key="tag" :text="tag" :removeDataTag="removeDataTag" :removeAllDataTags="removeAllDataTags" />
    </div>
    <span class="underline font-bold text-teal-500 cursor-pointer" @click="removeAllDataTags">Clear</span>
  </div>
</template>

<script>
import FilterTag from "./FilterTag.vue";
export default {
  props: {
    tags: { type: Array },
    removeDataTag: { type: Function},
    removeAllDataTags: { type: Function},
  },
    components: { FilterTag }
}
</script>

<style>
</style>