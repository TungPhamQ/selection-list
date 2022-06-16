<template>
  <div class="list-dropdown">
    <div class="list-scroll">
      <div v-for="province in apiFromSelect" :key="province.code">
        <label class="option">
          <input type="checkbox" :value=province.name v-model="selectedProvince">
          {{ province.name }}
        </label>
      </div>
    </div>
    <div class="button">
      <button @click="acceptSelection" class="button__accept">Đồng ý</button>
      <button @click="cancelSelection" class="button__cancel">Hủy</button>
    </div>

  </div>
</template>

<script>
// import CheckBox from './CheckBox.vue'

export default {
  name: 'ListDropdown',
  components: {
    // CheckBox
  },
  data() {
    return {
      selectedProvince: [],
    }
  },
  props: {
    apiFromSelect: Array,
  },
  computed: {

  },
  methods: {

    updateSelectedProvince(province) {
      const index = this.selectedProvince.indexOf(province);
      if (index == -1) {
        this.selectedProvince.push(province);
        console.log(this.selectedProvince)
      }
      else {
        this.selectedProvince.splice(index, 1);
        console.log(this.selectedProvince)
      }
    },
    acceptSelection() {
      this.$emit('updateProvince', this.selectedProvince);
    },
    cancelSelection() {
      this.selectedProvince = [];
      this.$emit('updateProvince', this.selectedProvince);
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list-dropdown {
  margin: auto;
  width: 100%;

  height: 304px;
  align-items: center;
  background: #FFFFFF;
  position: relative;
  box-shadow: 0px 1px 8px rgba(102, 102, 102, 0.2);
}

.list-scroll {
  overflow-y: scroll;
  height: 304px;
}
/* width */
::-webkit-scrollbar {
  width: 8px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #DCDCDC;
  border-radius: 6px;
}

.option {
  display: block;
  line-height: 10px;
  padding: 8px 0px;
}

.option:hover {
  background-color: #E7F1FD;
}

.button {
  position: absolute;
  bottom: 0px;
  background-color: #fff;
  display: block;
  width: 100%;

  padding: 8px 0px 16px 16px;
}

.button__accept {
  /* margin-top: 10px; */

  background-color: #007BC3;
  color: #fff;
  padding: 4px 19px;
  outline: none;
  border: 0px;
  border-radius: 4px;
  font-weight: 700;
  font-size: 16px;


  font-weight: 700;
  height: 32px;
  width: 104px;
}
input{
  padding-left: 19px;
}
.button__cancel {

  border: 0px;
  background-color: #fff;
  color: #007BC3;
  font-weight: 400;
  font-size: 16px;
  width: 82px;
  height: 24px;
}
</style>
