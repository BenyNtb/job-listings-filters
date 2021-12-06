<template>
    <div
        class="w-full h-28 flex items-center group bg-white rounded-md shadow-xl py-4 my-6 transform hover:-translate-y-2 transition duration-500">

        <div class="w-1.5 h-28 bg-white group-hover:bg-teal-500 rounded-l-md"></div>

        <img :src="require('@/assets/'+data.logo)" class="mx-8" alt />
        <div class="w-full flex justify-between items-center">

            <div class="flex flex-col justify-start">
                <div class="flex text-sm font-bold space-x-3">
                    <p class="text-teal-600">{{ data.company }}</p>
                    <span class="bg-teal-600 text-white py-1 px-2 rounded-full text-xs uppercase">New!</span>
                    <span class="bg-black text-white py-1 px-2 rounded-full text-xs uppercase">Featured</span>
                </div>

                <h2 class="text-gray-600 hover:text-teal-600 text-lg font-bold tracking-wide mt-2">{{ data.position }}
                </h2>

                <div class="flex text-gray-400 text-xs mt-2 font-bold">
                    {{ data.postedAt }}
                    <span class="mx-6">·</span>
                    {{ data.contract }}
                    <span class="mx-6">·</span>
                    {{ data.location }}
                </div>
            </div>
        </div>


        <div class="flex items-center space-x-3 mr-10">

            <JobTag v-for="text in getTags" :key="text" :text="text" @tag="$emit('tagsList', text)" />
        </div>
    </div>
</template>

<script>
    import JobTag from "./JobTag.vue";
    export default {
        props: ["data"],
        components: {
            JobTag
        },
        data() {
            return {
                bonjour: null,
            }
        },
        computed: {

            getTags() {
                return [this.data.role, this.data.level, ...this.data.languages, ...this.data.tools]
            }
        }
    }
</script>

<style>
</style>