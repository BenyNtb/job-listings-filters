<template>
  <div id="app">
    <Card v-for='data in datas' :key="data.company" :dataObj='data' @tags="add" />
    <Filter :tags="ajout" :removeDataTag="removeDataTag" :removeAllDataTags="removeAllDataTags" />
    <JobTag v-for="text in getTags" :key="text" :text="text" @tag="$emit('tagsList', text)" />
  </div>
</template>

<script>
  import Card from "./components/Card.vue";
  import Filter from './components/Filter.vue';
  import JobTag from "./JobTag.vue";
  import jsonDatas from '../exo-ressources/data.json'
  export default {
    name: 'App',
    components: {
      Card,
      Filter,
      JobTag,
    },
    data() {
      return {
        datas: jsonDatas,
        ajout: []
      }
    },
    methods: {
      add(value) {
        this.ajout = value;
        console.log(value);
      }
    },
  }
</script>

<style>
</style>