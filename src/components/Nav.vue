<template>
  <div class="nav">
    <el-dialog
      class="dialog"
      width="126px"
      top="44px"
      :show-close="false"
      :visible.sync="showNav">
      <div class="navList">
        <div class="list" @click="handleToDiv('vision')">{{ $t('nav.vision') }}</div>
        <div class="list" @click="handleToDiv('dfs')">{{ $t('nav.dfs') }}</div>
        <div class="list" @click="handleToDiv('project')">{{ $t('nav.project') }}</div>
        <div class="list">
          <span v-if="language !== 'en'" @click="handleChangeLang('en')">EN</span>
          <span v-else @click="handleChangeLang('zh-CN')">CN</span>
        </div>
      </div>
    </el-dialog>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      showNav: false,
    }
  },
  computed: {
    ...mapState({
      language: state => state.app.language,
    })
  },
  methods: {
    handleToDiv(name) {
      this.$emit('listenToDiv', name)
      this.showNav = false;
    },
    handleChangeLang(type) {
      this.showNav = false;
      this.$i18n.locale = type;
      this.$store.dispatch('setLanguage', type);
    },
  }
}
</script>

<style lang="scss" scoped>
.nav{
  position: relative;
  /deep/ .el-dialog{
    position: absolute;
    border-radius: 8px;
    right: 8px;
    .el-dialog__header{
      padding: 0;
    }
    .el-dialog__body{
      padding: 20px 5px 10px;
    }
  }
  .navList{
    color: #070707;
    .list{
      font-size: 14px;
      font-weight: 500;
      height: 44px;
      display: flex;
      align-items: center;
      justify-content: center;
      .github{
        color: #070707;
        text-decoration: none;
      }
    }
  }
}
</style>
