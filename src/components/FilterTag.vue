<template>
    <div class="flex h-6 items-center group cursor-pointer" @click="removeDataTag">
        <p
            class="px-2 py-1.5 h-full m-0 rounded-l-md bg-teal-100 font-bold text-teal-600 text-xs flex justify-center items-center">
            {{ text }}</p>
        <img src="../assets/icon-remove.svg"
            class="bg-teal-500 group-hover:bg-black fill-current h-full p-1.5 rounded-r-md" alt />
    </div>
</template>

<script>
    export default {
        props: {
            text: {
                type: String
            },
            removeDataTag: {
                type: Function
            },
        }
    }
</script>

<style>
</style>