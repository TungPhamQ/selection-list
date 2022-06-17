<template>
  <div id="app">
    <ProvinceSelection :apiFromApp="listProvinces"></ProvinceSelection>
  </div>
</template>

<script>
import ProvinceSelection from './components/ProvinceSelection.vue'
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      listProvinces: null,
    }
  },
  components: {
    ProvinceSelection,
  },
  mounted() {
    axios
      .get('https://provinces.open-api.vn/api/')
      .then(response => (this.listProvinces = response.data))
  },
  methods: {
    log: function () {
      console.log(this.listProvinces)
    }
  }

}
</script>

<style >
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;200;300;400;500;600;700;800&display=swap');

#app {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Noto Sans', sans-serif;
}
</style>
