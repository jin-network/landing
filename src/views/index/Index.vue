<template>
  <div class="borrow">
    <my-header @listenToDiv="handleToDiv"/>
    <div class="dapp" ref="dapp">
      <div class="minW flexB">
        <div class="dappContent">
          <div>一个整合了一系列</div>
          <div class="mb30">DeFi协议的区块链开放金融网络</div>
          <div><button class="btn">立即体验 ></button></div>
        </div>
        <div class="contentImg">
          <img width="100%" src="@/assets/img/1.png" alt="">
        </div>
      </div>
    </div>
    <!-- 项目愿景 -->
    <div class="vision" ref="vision">
      <div class="minW flexB">
        <div class="vCont">
          <div class="title">让全世界每个角落的人</div>
          <div class="title mb30">都能享受到安全、平等的金融服务</div>
          <div class="tip mb15">
            传统的金融基础设施由于受到文化差异和主权管辖的地域限制，彼此是互相孤立、碎片化的。
            而基于区块链技术的开放金融网络，将为传统金融基础设施带来革命性的改变。
            这个网络可以打破国际金融壁垒，汇集全球流动性，创造出网络效应，在全球范围内开创货币和金融的可编程性。
          </div>
          <div class="link"><span>阅读白皮书 ></span></div>
        </div>
        <div class="contentImg">
          <img width="100%" src="@/assets/img/2.png" alt="">
        </div>
      </div>
    </div>
    <!-- DFS代币 -->
    <div class="dfs" ref="dfs">
      <div class="minW flexB">
        <div class="contentImg">
          <img width="100%" src="@/assets/img/3.png" alt="">
        </div>
        <div class="vCont">
          <div class="title">DFS代币</div>
          <div class="title mb30">用于交易、社区治理、流动性激励、协议费分红、抵押发行合成资产等</div>
          <div class="tip mb15">
            通过整合一系列DeFi协议，DeFis Network未来在区块链金融领域将形成强大的网络效应。
            而平台币HYK将会持续捕获这些DeFi协议产生的价值。DFS持有者将持续获得协议费的分红。
            通过智能合约自动执行分红，让每个持有者，都能公平分享到DeFis Network发展的红利。
          </div>
        </div>
      </div>
    </div>
    <!-- 项目进度 -->
    <div class="project" ref="project">
      <div class="title">项目进度</div>
      <div class="proList flexB">
        <div class="item">
          <div class="">
            <div class="itemImg"><img src="@/assets/img/swap.png" width="100%" alt=""></div>
            <div class="name">SWAP</div>
            <div class="status">已上线</div>
          </div>
          <div class="bgImg"><img width="100%" src="@/assets/img/4.png" alt=""></div>
        </div>
        <div class="item">
          <div>
            <div class="itemImg"><img src="@/assets/img/bank.png" width="100%" alt=""></div>
            <div class="name">SWAP</div>
            <div class="status">已上线</div>
          </div>
          <div class="bgImg"><img width="100%" src="@/assets/img/5.png" alt=""></div>
        </div>
        <div class="item">
          <div>
            <div class="itemImg"><img src="@/assets/img/LEND.png" width="100%" alt=""></div>
            <div class="name">SWAP</div>
            <div class="status">已上线</div>
          </div>
          <div class="bgImg"><img width="100%" src="@/assets/img/6.png" alt=""></div>
        </div>
        <div class="item">
          <div>
            <div class="itemImg"><img src="@/assets/img/synthetix.png" width="100%" alt=""></div>
            <div class="name">SWAP</div>
            <div class="status">已上线</div>
          </div>
          <div class="bgImg"><img width="100%" src="@/assets/img/7.png" alt=""></div>
        </div>
      </div>
    </div>
    <my-footer ref="question"/>

    <transition name="el-fade-in-linear">
      <div class="toTop" v-if="showToTop" @click="handleBackTop">
        <span class="iconfont icon-huaban35 top"></span>
      </div>
    </transition>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader'
import MyFooter from './components/MyFooter'
export default {
  name: 'index',
  components: {
    MyHeader,
    MyFooter,
  },
  data() {
    return {
      scrollTop: 0,
      showToTop: false,
      timer: null,
    }
  },
  computed:{
  },
  props: {
  },
  watch: {
  },
  mounted() {
    window.addEventListener('scroll', this.scrollToTop);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.scrollToTop)
    clearInterval(this.timer);
  },
  methods: {
    handleToDiv(refName) {
      clearInterval(this.timer);
      let t = 0
      this.timer = setInterval(() => {
        t += 1;
        const ispeed = Math.ceil((this.$refs[refName].offsetTop - this.scrollTop) / 5);
        document.documentElement.scrollTop = this.scrollTop + ispeed; // eslint-disable-line
        if (this.scrollTop >= this.$refs[refName].offsetTop || t > 20) {
          clearInterval(this.timer);
        }
      }, 10)
    },
    // 回到顶部
    handleBackTop() {
      clearInterval(this.timer);
      const timer = setInterval(() => {
        const ispeed = Math.floor(-this.scrollTop / 5);
        document.documentElement.scrollTop = this.scrollTop + ispeed; // eslint-disable-line
        if (this.scrollTop === 0) {
          clearInterval(timer);
        }
      }, 10)
    },
    // 监听滚动事件
    scrollToTop() {
      const scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
      this.scrollTop = scrollTop
      if (this.scrollTop > 240) {
        this.showToTop = true
      } else {
        this.showToTop = false
      }
    },
  }
}
</script>

<style lang="scss" scoped>
.borrow{
  color: #000;
  .minW{
    min-width: 1200px;
    width: 1200px;
    margin: auto;
    padding: 0px 0px 66px 70px;
    box-sizing: border-box;
    text-align: left;
  }
  .flexB{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .flexC{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  .mb30{
    margin-bottom: 30px !important;
  }
  .mb15{
    margin-bottom: 15px !important;
  }
  .blod{
    font-weight: bold;
  }
  .dappContent{
    font-size: 24px;
    font-weight: bold;
    text-align: left;
    letter-spacing: 1.11px;
    .btn{
      color: #57BB9B;
      border: 1px solid #57BB9B;
      border-radius: 2px;
      font-size: 14px;
      background: transparent;
      height: 40px;
      padding: 0px 20px;
      outline: none;
      cursor: pointer;
    }
  }
  .contentImg{
    width: 600px;
    height: 400px;
  }
  .vision,.dfs{
    background: #fafafa;
    padding: 100px 0px;
    .vCont{
      max-width: 500px;
      .title{
        font-size: 20px;
        font-weight: bold;
        letter-spacing: 1.11px;
      }
      .tip{
        font-size: 14px;
        color: #999;
        letter-spacing: 0.78px;
      }
      .link{
        font-size: 14px;
        font-weight: bold;
        color: #57BB9B;
      }
    }
  }
  .dfs{
    background: #FFF;
  }
  .project{
    background: #fafafa;
    padding: 100px 0px;
    .title{
      font-size: 20px;
      letter-spacing: 1.11px;
      font-weight: bold;
      margin-bottom: 47px;
    }
    .proList{
      width: 1200px;
      margin: auto;
      .item{
        background: #FFF;
        position: relative;
        width: 200px;
        height: 380px;
        display: flex;
        align-items: center;
        justify-content: center;
        &>div:first-child{
          position: relative;
          z-index: 2;
        }
        .itemImg{
          margin: auto;
          width: 60px;
          height: 60px;
          margin-bottom: 6px;
        }
        .status{
          font-size: 14px;
          color: #999999;
          letter-spacing: 0.78px;
          margin-top: 7px;
        }
        .name{
          font-size: 20px;
          font-weight: bold;
          letter-spacing: 1.11px;
        }
        .bgImg{
          position: absolute;
          bottom: 0px;
          z-index: 1;
        }
      }
    }
  }

  .toTop{
    position: fixed;
    bottom: 120px;
    right: 120px;
    z-index: 10;
    background: #FFF;
    height: 50px;
    width: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    box-shadow: 0 0 5px 0px #999;
    .top{
      font-size: 12px;
      color: #57BB9B
    }
  }
}
</style>
