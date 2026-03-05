<template>
  <div class="login-container">
    <div class="login-card">
      <div class="card-header">
        <h2 class="title">欢迎回来</h2>
        <p class="subtitle">请登录您的账号</p>
      </div>

      <el-form
          ref="loginForm"
          :model="loginForm"
          :rules="rules"
          class="login-form"
          label-position="top"
          @keyup.enter="submitForm('loginForm')"
      >
        <el-form-item prop="username">
          <el-input
              v-model="loginForm.username"
              placeholder="账号"
              size="large"
              clearable
          >
            <template #prefix>
              <i class="iconfont icon-r-user1" style="font-size: 20px; color: #909399;"></i>
            </template>
          </el-input>
        </el-form-item>

        <el-form-item prop="password">
          <el-input
              v-model="loginForm.password"
              type="password"
              placeholder="密码"
              size="large"
              show-password
              clearable
          >
            <template #prefix>
              <i class="iconfont icon-r-lock" style="font-size: 20px; color: #909399;"></i>
            </template>
          </el-input>
        </el-form-item>

        <el-form-item>
          <el-button
              type="primary"
              size="large"
              class="submit-btn"
              :loading="loading"
              @click="submitForm('loginForm')"
          >
            登录
          </el-button>
        </el-form-item>

        <div class="form-footer">
          <el-link type="primary" :underline="false">忘记密码？</el-link>
          <el-link type="primary" :underline="false">注册账号</el-link>
        </div>
      </el-form>
    </div>
  </div>
</template>

<script>
import { ajaxPost, popup } from "@/assets/js/common";
import Cookies from "js-cookie";

export default {
  name: "Login",
  data() {
    return {
      loginForm: {
        username: "",
        password: "",
      },
      loading: false,
      rules: {
        username: [
          { required: true, message: "账号不能为空", trigger: "blur" },
        ],
        password: [
          { required: true, message: "密码不能为空", trigger: "blur" },
          { min: 5, max: 8, message: "密码长度为5-8位", trigger: "blur" },
        ],
      },
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.loading = true;
          ajaxPost("/login", this.loginForm)
              .then((res) => {
                res = res.data;
                if (res.code == 200) {
                  Cookies.set("token", res.data.token, {
                    expires: 1 / 48,
                  });
                  Cookies.set(
                      "employee",
                      JSON.stringify(res.data.employee),
                      { expires: 1 / 48 }
                  );
                  popup("登录成功，请稍等...");
                  this.$router.push("/index");
                } else {
                  popup(res.msg, "warning");
                }
              })
              .finally(() => {
                this.loading = false;
              });
        } else {
          popup("账号或密码格式不正确！", "error");
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
  },
};
</script>

<style scoped>
.login-container {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding-right:10%;
  background: url("../assets/bg1.png") center/cover no-repeat;
  position: relative;
  overflow: hidden;
}

/* 动态背景装饰 */
.login-container::before {
  content: "";
  position: absolute;
  width: 200%;
  height: 200%;
  background: rgba(255, 255, 255, 0.1);
  margin-right:15%;
  transform: rotate(45deg);
  top: -50%;
  left: -50%;
  z-index: 1;
}

.login-card {
  width: 420px;
  max-width: 90%;
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(10px);
  border-radius: 24px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
  padding: 40px 35px;
  z-index: 2;
  animation: fadeInUp 0.6s ease;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.card-header {
  text-align: center;
  margin-bottom: 30px;
}

.title {
  font-size: 32px;
  font-weight: 600;
  color: #303133;
  margin: 0 0 8px 0;
  letter-spacing: 1px;
}

.subtitle {
  font-size: 14px;
  color: #909399;
  margin: 0;
}

.login-form {
  margin-top: 20px;
}

/* 调整输入框样式，与图标和谐共存 */
:deep(.el-input__wrapper) {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  border-radius: 12px;
  transition: box-shadow 0.2s;
  padding-left: 8px; /* 为图标留出更多空间 */
}

:deep(.el-input__wrapper:hover) {
  box-shadow: 0 2px 12px rgba(102, 126, 234, 0.2);
}

:deep(.el-input__wrapper.is-focus) {
  box-shadow: 0 2px 12px rgba(102, 126, 234, 0.3);
}

:deep(.el-input__prefix) {
  display: flex;
  align-items: center;
  margin-right: 6px;
}

.submit-btn {
  width: 100%;
  height: 48px;
  font-size: 18px;
  border-radius: 12px;
  background: blue;
  border: none;
  transition: transform 0.2s, box-shadow 0.2s;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 20px rgba(102, 126, 234, 0.4);
}

.submit-btn:active {
  transform: translateY(0);
}

.form-footer {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
  font-size: 14px;
}

.form-footer .el-link {
  color: #667eea;
}

.form-footer .el-link:hover {
  color: #764ba2;
}
</style>