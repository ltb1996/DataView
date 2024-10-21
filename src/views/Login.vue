<template>
  <div class="login-container">
    <video id="v1" autoplay muted loop class="background-video">
      <source
        src="https://sf3-cdn-tos.toutiaostatic.com/obj/mp/welcome-video.mp4"
      />
    </video>
    <div class="login-title"></div>
    <form class="login-form" @submit.prevent="login">
      <div class="form-group">
        <label for="username">用户名</label>
        <input type="text" id="username" v-model="username" required />
      </div>
      <div class="form-group">
        <label for="password">密码</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <button type="submit" class="login-button">登录</button>
    </form>
    <p class="forgot-password">忘记密码？</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      errorMessage: "", // 添加错误信息
    };
  },
  methods: {
    // 登录方法
    login() {
      // 登录逻辑
      if (this.username === "admin" && this.password === "admin") {
        this.$router.push("/index");
      } else {
        this.errorMessage = "用户名或密码错误";
        alert(this.errorMessage); // 提示错误信息
      }
    },
  },
};
</script>

<style scoped>
.login-container {
  position: relative; /* 使子元素可以绝对定位 */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden; /* 防止视频溢出 */
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    "Helvetica Neue", Arial, sans-serif;
}

.background-video {
  position: absolute; /* 绝对定位 */
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover; /* 保持视频比例并覆盖整个容器 */
  z-index: 1; /* 设置为背景 */
}

.login-title {
  font-size: 2.5rem;
  margin-bottom: 20px;
  color: #fff; /* 修改为白色以便在视频上可见 */
  z-index: 99;
  background: url(../assets/img/logo3.png) center center no-repeat;
  background-size: 30%; /* 调整背景图像大小为30% */
  width: 100%; /* 设置宽度为100% */
  height: 80px; /* 调整高度以适应更小的背景图像 */
  display: flex; /* 使用flex布局 */
  align-items: center; /* 垂直居中对齐 */
  justify-content: center; /* 水平居中对齐 */
}

.login-form {
  width: 300px; /* 可以根据需要调整 */
  background: rgba(255, 255, 255, 0.8); /* 半透明背景 */
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  z-index: 99;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input {
  width: 90%; /* 修改为80%以缩短输入框 */
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 1rem;
}

input:focus {
  border-color: #007aff;
  outline: none;
}

.login-button {
  width: 90%;
  padding: 10px;
  background-color: #007aff;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
}

.login-button:hover {
  background-color: #005bb5;
}

.forgot-password {
  margin-top: 10px;
  color: #007aff;
  cursor: pointer;
  z-index: 99;
}
</style>
