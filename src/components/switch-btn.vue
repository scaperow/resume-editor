<template>
  <span class="switch-btn" :class="{on: status}" @click="onSwitch"></span>
</template>

<script>
export default {
  props: ['value'],
  data () {
    return {
      status: this.value || false
    }
  },
  methods: {
    onSwitch (e) {
      this.status = !this.status
      this.$emit('toggle')
    }
  },
  watch: {
    value: function (value) {
      this.status = value
    }
  }
}
</script>

<style lang="scss">
  .switch-btn{
    display: inline-block;
    position: relative;
    width: 40px;
    height: 20px;
    border: 1px solid #dcdfe6;
    outline: none;
    border-radius: 10px;
    box-sizing: border-box;
    background: #dcdfe6;
    cursor: pointer;
    transition: border-color .3s,background-color .3s;
    vertical-align: middle;
  }
  .switch-btn.on{
    border-color: rgb(19, 206, 102);
    background-color: rgb(19, 206, 102);
  }
  .switch-btn:after {
    content: "";
    position: absolute;
    top: 1px;
    left: 1px;
    border-radius: 100%;
    transition: all .3s;
    width: 16px;
    height: 16px;
    background-color: #fff;
  }
  .switch-btn.on:after {
    left: 100%;
    margin-left: -17px;
  }
</style>
