<template>
  <div class="check-box">
    <label >
      <input type="checkbox" :value=province.name v-model="selectedProvince" @change="acceptSelection">
      {{ province.name }}
    </label>
  </div>
</template>

<script>
export default {
  name: 'CheckBox',
  data() {
    return {
      selectedProvince : [],
    }
  },
  props: {
    province: Object, 
  },
  computed: {

  },
  methods: {
    acceptSelection(){
      this.$emit('updateToListDropdown', this.selectedProvince);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
