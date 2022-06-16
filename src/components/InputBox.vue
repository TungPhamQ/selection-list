<template>
  <div>
    <input type="text" class="input-box" placeholder="Chọn tỉnh thành:">
  </div>
</template>

<script>
export default {
  name: 'InputBox',
  props: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{
  padding: 0px
}
.input-box {
  width: 470px;
  height: 48px;
  border: 1px solid #999;
  border-radius: 4px;

  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  padding-left: 10px;
}

.input-box:focus {
  border: 1px solid #007BC3;
  box-shadow: 0px 0px 8px rgba(0, 123, 195, 0.32);
  border-radius: 4px;
  outline: none;
}
</style>
