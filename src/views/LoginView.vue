<script>

export default {
  data() {
    return {
      image: [
        require('@/assets/image/bg.jpg'),
        require('@/assets/image/login-bg1.jpg'),
        require('@/assets/image/login-bg2.jpg'),
        require('@/assets/image/login-bg3.jpg'),
        require('@/assets/image/login-bg4.jpg'),
      ],
      // 抽屉
      registerDrawer: false,
      labelPosition: 'top',
      loginForm: {
        username: '',
        password: ''
      },
      registerForm: {
        username: '',
        email: '',
        password: '',
        confirmPassword: ''
      }
    };
  },
  methods: {
    handleLogin() {
      // 登录逻辑处理
      alert('登录成功');
    },
    handleRegister() {
      // 注册逻辑处理
      alert('注册成功');
    }
  }
}
</script>

<template>
  <div id="app">
    <div class="login-container">

      <!-- 登录界面图片走马灯 -->
      <div class="login-img">
        <el-carousel :interval="4000" type="card" height="500px">
          <el-carousel-item v-for="(item, index) in image" :key="index">
            <img :src="item" alt="" style="width: 100%; height: 100%; object-fit: cover" />
          </el-carousel-item>
        </el-carousel>
      </div>

      <!-- 登录界面 -->
      <div>
        <div class="login-box">
          <div class="login-sakura">Sakura🌸</div>
          <div class="login-main">
            <el-form :label-position="labelPosition" label-width="80px" :model="loginForm">
              <el-form-item label="Email/Phone">
                <el-input v-model="loginForm.username" placeholder="请输入账号"></el-input>
              </el-form-item>
              <el-form-item label="Password">
                <el-input v-model="loginForm.password" show-password placeholder="请输入密码"></el-input>
              </el-form-item>
              <div class="login-button">
                <el-button type="success" class="login-btn" @click="handleLogin"> <i class="el-icon-s-promotion"></i>登录</el-button>
                <el-button class="login-btn" @click="registerDrawer = true" type="primary" style="margin-left: 16px;"><i class="el-icon-circle-plus"></i>注册</el-button>
              </div>
              <div class="img-item">Sakura © 2024 SOUNDCLOUD</div>
            </el-form>
          </div>
        </div>
      </div>
    </div>

    <!-- 注册抽屉 -->
    <el-drawer
        title="注册🌸"
        direction="rtl"
        :visible.sync="registerDrawer"
        :with-header="true">
      <div>
        <div class="login-box">
          <div class="login-sakura">Sakura🌸</div>
          <div class="login-main">
            <el-form :label-position="labelPosition" label-width="80px" :model="registerForm">
              <el-form-item label="昵称">
                <el-input v-model="registerForm.username" placeholder="请输入用户名"></el-input>
              </el-form-item>
              <el-form-item label="Email/Phone">
                <el-input v-model="registerForm.email" placeholder="请输入邮箱"></el-input>
              </el-form-item>
              <el-form-item label="密码">
                <el-input v-model="registerForm.password" show-password placeholder="请输入密码"></el-input>
              </el-form-item>
              <el-form-item label="确认密码">
                <el-input v-model="registerForm.confirmPassword" show-password placeholder="请确认密码"></el-input>
              </el-form-item>
              <div class="register-button">
                <el-button type="primary" class="register-btn" @click="handleRegister"><i class="el-icon-circle-plus"></i>注册</el-button>
                <el-button type="success" class="reset-btn"  native-type="reset"> <i class="el-icon-s-promotion"></i>重置</el-button>
              </div>
            </el-form>
          </div>
        </div>
      </div>
    </el-drawer>
  </div>
</template>

<style scoped>

@font-face {
  font-family: 'CakeCafe';
  src: url('@/assets/style/fonts/Cakecafe.ttf');
}

#app {
  position: absolute;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  background: url("@/assets/image/login-bg3.jpg");
  background-size: cover;
}

.login-container {
  width: 80%;
  max-width: 1400px;
  height: 600px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 10px 10px 10px rgba(0,0,0,.3);
  border-radius: 10px;
  border-top: 3px solid pink;
  display: flex;
  opacity: .9;
  overflow: hidden;
}

.login-img, img {
  margin-top: 30px;
  padding-left: 5px;
  width: 900px;
  height: 305px;
  padding-right: 10px;
}

.img-item {
  font-family: 'CakeCafe', serif;
  text-align: center;
  margin-top: 60px;
  color: pink;
  text-shadow: 10px 10px 10px pink;
}
.login-box {
  height: 500px;
  width: 330px;
  margin-left: 60px;
}

.login-sakura {
  margin: 20px auto;
  width: 300px;
  height: 80px;
  text-align: center;
  font-size: 40px;
  font-family: 'CakeCafe', serif;
  line-height: 80px;
  color: pink;
  text-shadow: 10px 10px 10px pink;

}

i {
  padding-right: 8px;
}

.login-btn, .register-btn {
  width: 156px;
}

.login-button, .register-button {
  margin-top: 60px;
  display: flex;
  justify-content: space-between;
}

.el-carousel__item h3 {
  color: #475669;
  font-size: 14px;
  opacity: 0.75;
  line-height: 200px;
  margin: 0;
}

</style>
