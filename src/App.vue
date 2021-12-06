<template>
  <div id="app">
    <div class="container">
      <Filter
        :tags="tagsList"
        :removeDataTag="removeDataTag"
        :removeAllDataTags="removeAllDataTags"
      />
      <Card
        v-for="data in jobDatas"
        :key="data.company"
        :data="data"
        @tagsList="dataTagsList"
        :tagsList="tagsList"
      />

    </div>
  </div>
</template>

<script>
import Card from './components/Card.vue';
import Filter from './components/Filter.vue';
import data from '../exo-ressources/data.json';

export default {
  name: "App",
  data () {
    return {
      datas: data,
      tagsList: [],
    }
  },
  components: { Filter, Card },
  methods: {
    dataTagsList: function (tag) {
      let tagsList = this.tagsList
      if (this.tagsList.every(e => e != tag) == true) {
        tagsList = [...this.tagsList, tag];
      }
      else if (this.tagsList.every(e => e !== tag) == false) {
        tagsList.splice([...this.tagsList].indexOf(tag), 1);
      }
      this.tagsList = [...new Set(tagsList)]
    },
    removeDataTag: function (tag) {
      this.tagsList.splice(this.tagsList.indexOf(tag), 1);
    },
    removeAllDataTags: function () {
      this.tagsList = [];
    },
  },
    computed: {
    jobDatas: function () {
      return [...this.datas].filter(data =>
        this.tagsList.every(e =>
          [data.role, data.level, ...data.languages, ...data.tools].includes(e)
        )
      );
    },
  },
}
</script>

<style lang="sass" scoped>

#app
  min-height: 100vh
  width: 100%
  margin: 0 auto
  display: flex
  flex-direction: column
  align-items: center
  &::before
    content: ''
    display: block
    position: absolute
    top: 0
    width: 100%
    height: 155px
    background-repeat: none
  .container
    z-index: 10
</style>
