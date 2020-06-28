<template>
  <div class="header">
    <div class="minW flexB">
      <div class="logo"><img src="@/assets/img/defis.png" alt=""></div>
      <div class="nav flexB">
        <span @click="handleToDiv('vision')">项目愿景</span>
        <span @click="handleToDiv('dfs')">DFS代币</span>
        <span @click="handleToDiv('project')">项目进度</span>
        <span>常见问题</span>
        <span>EN / CN</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'myHeader',
  data() {
    return {
    }
  },
  methods: {
    handleToDiv(name) {
      this.$emit('listenToDiv', name)
    }
  }
}
</script>

<style lang="scss" scoped>
.header{
  padding: 13px auto;
  .minW{
    min-width: 1200px;
    width: 1200px;
    margin: auto;
  }
  .flexB{
    display: flex;
    align-content: center;
    justify-content: space-between;
  }
  .logo{
    height: 60px;
    width: 200px;
    img{
      width: 100%;;
    }
  }
  .nav{
    span{
      color: #000;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-left: 30px;
      font-size: 16px;
      font-weight: bold;
      letter-spacing: 0.89px;
      cursor: pointer;
    }
  }
}
</style>