<template>
  <div class="footer">
    <div class="minW flexB">
      <div class="logo"><img src="@/assets/img/defis.png" alt=""></div>
      <div class="nav flexB">
        <!-- <span>常见问题</span> -->
        <span>Copyright © 2020 DeFis.Network All rights reserved.</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'myFooter',
  data() {
    return {}
  }
}
</script>

<style lang="scss" scoped>
.footer{
  margin: 13px auto;
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
      color: #999;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-left: 30px;
      font-size: 14px;
      font-weight: bold;
      letter-spacing: 0.89px;
      cursor: pointer;
    }
  }
}
</style>
