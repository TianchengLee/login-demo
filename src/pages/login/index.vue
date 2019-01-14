<template>
  <div class="login-container">
    <h1 class="title">登陆</h1>
    <el-form :label-position="labelPosition" label-width="80px">
      <el-form-item label="用户名">
        <el-input v-model="username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input @keydown.native.enter="login" type="password" v-model="password"></el-input>
      </el-form-item>
      <el-button type="primary" @click="login">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      labelPosition: "left",
      username: "",
      password: ""
    };
  },
  methods: {
    login() {
      console.log("执行登录操作");
      if (!this.username.trim() || !this.password.trim())
        return this.$message({
          message: "请输入用户名或密码哦!",
          type: "warning"
        });

      this.$http
        .post("/users/login", {
          username: this.username,
          password: this.password
        })
        .then(result => {
          // console.log(result);
          let userInfo = result.data.data;
          // let tokenStr = userInfo.token;
          // localStorage.setItem("token", tokenStr);
          // localStorage.setItem("userInfo", JSON.stringify(userInfo));
          // 将token存储到Vuex的store中
          // 不推荐, 只要涉及到操作state的数据, 应该都在mutations中定义好操作的方法后再去触发
          // this.$store.state.token = tokenStr
          // 提交一个任务给mutations进行执行
          this.$store.commit("setUserInfoAndToken", userInfo);
          // 登录成功提醒用户
          // alert(result.data.succMsg);
          // 将Token存储到localStorage
          this.$message({
            message: result.data.succMsg,
            type: "success"
          });
          // 登录成功跳转到首页
          this.$router.push("/home");
        })
        // .then的回调函数有两个, 第一个是成功的, 第二个是失败的
        // 但是如果失败了也会报错, 通过.catch也可以进行捕获
        .catch(err => {
          // console.log(error.response.data.errMsg);
          this.$message.error("恭喜您哦!" + err.response.data.errMsg);
        });
    }
  }
};
</script>

<style lang="less" scoped>
.login-container {
  width: 500px;
  margin: 100px auto;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 30px;
  box-shadow: 0 0 10px #ccc;
  .title {
    font-size: 24px;
    font-weight: bold;
    padding-bottom: 15px;
  }
}
</style>
