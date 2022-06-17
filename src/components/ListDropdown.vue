<template>
  <div class="list-dropdown" v-show="isShow">
    <div class="list-scroll">
      <div v-for="province in apiFromProvinceSelection" :key="province.code">
        <label class="option  container">
          <input type="checkbox" checked="checked" :value=province.name v-model="selectedProvince">
          <span class="checkmark"></span>
          {{ province.name }}
        </label>
      </div>
    </div>
    <div class="button">
      <button @click="acceptSelection(), showList()" class="button__accept">Đồng ý</button>
      <button @click="cancelSelection(), showList()" class="button__cancel">Hủy</button>
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
    apiFromProvinceSelection: Array,
    isShow: Boolean,
  },
  computed: {

  },
  methods: {

    updateSelectedProvince(province) {
      const index = this.selectedProvince.indexOf(province);
      if (index == -1) {
        this.selectedProvince.push(province);
        // console.log(this.selectedProvince)
      }
      else {
        this.selectedProvince.splice(index, 1);
        // console.log(this.selectedProvince)
      }
    },
    acceptSelection() {
      this.$emit('updateProvince', this.selectedProvince);
    },
    cancelSelection() {
      this.selectedProvince = [];
      this.$emit('updateProvince', this.selectedProvince);
    },
    showList() {
      this.$emit('showList');
      // console.log(this.isShow);
    }

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

input {
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

/* Custom checkbox */
/* The container */
.container {
  display: block;
  position: relative;
  padding: 0px 0px 0px 48px;
  line-height: 40px;
  margin-bottom: 0;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 11px;
  left: 19px;
  height: 18px;
  width: 18px;
  background-color: #eee;
}

/* On mouse-over, add a grey background color */
.container:hover input~.checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.container input:checked~.checkmark {
  background-color: #45D1C9;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked~.checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
  left: 4px;
  top: 2px;
  width: 6px;
  height: 8px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>
