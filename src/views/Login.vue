<template>
  <div class="bg" :height="fullHeight" :width="fullWidth">
    <div class="img_box">
      <!-- 背景图片：动态绑定宽高 -->
      <!-- <img src="../../assets/img/bg01.png" :width="fullWidth" /> -->
      <img src="../assets/backimg.png" :width="fullWidth" />
      <el-container>
        <el-row style="display: flex;margin: auto;text-align: center">
          <div style="margin-top: 150px;">
            <el-form ref="form" :model="form">
              <h3>管 理 后 台 登 陆</h3>
              <el-form-item prop="username" required>
                <el-input type="text" clearable v-model="form.username" prefix-icon="el-icon-user-solid" placeholder="账号" style="width: 100%;"></el-input>
              </el-form-item>
              <el-form-item prop="password" required>
                <el-input type="password" clearable v-model="form.password" show-password prefix-icon="el-icon-s-help" placeholder="密码" style="width: 100%;"></el-input>
              </el-form-item>
              <el-button type="primary" style="width: 100%">登 录</el-button>
              <br style="margin: 5px"/>
              <br style="margin: 5px"/>
              <el-button type="primary" style="width: 100%" @click="toSystem()">免 登 录 按 钮</el-button>
            </el-form>
          </div>
        </el-row>
      </el-container>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      form: {
        username: '',
        password: ''
      },
      // 获取设备宽度、高度
      fullWidth: document.documentElement.clientWidth,
      fullHeight: document.documentElement.clientHeight
    }
  },
  created () {
    // 添加监听，监听设备宽高
    window.addEventListener('resize', this.handleResize)
  },
  beforeDestroy: function () {
    // 销毁监听
    window.removeEventListener('resize', this.handleResize)
  },
  methods: {
    onSubmit () {
      console.log('submit!')
    },
    handleResize (event) {
      this.fullWidth = document.documentElement.clientWidth - 16
      this.fullHeight = document.documentElement.clientHeight - 16
      this.curWidth = this.fullWidth + 'px'
      this.curHeight = this.fullHeight + 'px'
    },
    toSystem () {
      this.$router.push({ path: '/system' })
    }
  }
}
</script>

<style scoped>
.bg{
  padding: 0;
  margin: 0;
}
.bg .img_box{
  width: 100%;height: 100%;
}
.bg .img_box img{
  position: fixed; /* 固定图片位置 */
}
</style>
