<template>
  <div class="province-selection">
    <InputBox> </InputBox>
    <ListDropdown :apiFromSelect="apiFromApp" @updateProvince="handleSelected"></ListDropdown>
    <!-- <ResultBox> </ResultBox> -->
    <div class="result-box">
      <div v-for="province in selectedProvince" :key="province.code">
        <p> {{ province }} </p>
      </div>
    </div>
  </div>
</template>

<script>
import InputBox from './InputBox.vue'
// import ResultBox from './ResultBox.vue'
import ListDropdown from './ListDropdown.vue'

export default {
  name: 'ProvinceSelection',
  components: {
    InputBox,
    ListDropdown,
    // ResultBox
  },
  data() {
    return {
      selectedProvince: null,
    }
  },
  props: {
    apiFromApp: Array,
  },
  methods: {
    handleSelected(event) {
      this.selectedProvince = event;
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.province-selection {
  margin: auto;
  width: 480px;
  box-sizing: border-box;
} 

.result-box {
  border: 1px solid #999999;
  margin-top: 8px;
  height: 48px;
  width: 100%;
  cursor: pointer;
  align-items: center;
  border-radius: 4px;
}
</style>
