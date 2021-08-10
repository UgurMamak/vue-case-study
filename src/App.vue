<template>
  <div id="app">
    <Tags v-model="tags" color="primary"/>
    <Tags v-model="tags2" color="secondary"/>
    <Tags/>
  </div>
</template>

<script>
import Tags from "./components/Tags"
export default {
  data () {
    return {
      tags:"deneme1,test1",
      tags2:"deneme2,test2"
    }
  },
  components: {
    Tags
  }
}
</script >

<style>

</style>
