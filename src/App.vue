<template>
  <div id="app">
    <brandList></brandList>
  </div>
</template>

<script>
import brandList from './brand/brand_list.vue';
export default {
  data () {
    return {
      msg: 'Want something new?'
    }
  },

  methods: {
    startHacking () {
      this.$notify({
        title: 'Shhh',
        message: 'Just be patient...',
        duration: 6000
      })
    }
  },

  components:{
    brandList
  }

}
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
</style>
