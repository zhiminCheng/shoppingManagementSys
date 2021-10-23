<template>
    <div class="login_container">
        <div class="login_box">
            <!-- 头像图标 -->
            <div class="avater_box">
                <img src="../../assets/image/logo.jpg" alt="logo"/>
            </div>
            <!-- 登录表单 -->
            <div>
                <el-form ref="loginFormRef" :model="loginForm" :rules="loginRules" label-width="0px" class="loginForm">
                    <!-- 用户名称 -->
                    <el-form-item prop="username">
                        <el-input v-model="loginForm.username" prefix-icon="iconfont icon-account-fill" placeholder="user name"></el-input>
                    </el-form-item>
                    <!-- 密码 -->
                    <el-form-item prop="password">
                        <el-input v-model="loginForm.password" prefix-icon="iconfont icon-password" placeholder="password" type="password"></el-input>
                    </el-form-item>
                    <!-- 按钮 -->
                    <el-form-item class="btns">
                        <el-button type="primary" plain @click="submitForm('loginFormRef')">登录</el-button>
                        <el-button type="primary" plain @click="resetForm('loginFormRef')">重置</el-button>
                    </el-form-item>
                </el-form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
   data() {
      return {
        loginForm: {
          username: '',
          password: ''
        },
        loginRules: {
            username: [
              { required: true, message: '请输入登录名称', trigger: 'blur' },
              { min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur' }
            ],
            password: [
              { required: true, message: '请输入登录密码', trigger: 'blur' },
              { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
            ]
        }
      }
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
}
</script>
<style lang="less" scoped>
    .login_container{
        height: 100%;
        background-color: #2b4b6b;
    }
    .login_box{
        width: 450px;
        height: 300px;
        background-color: #fff;
        border-radius: 3px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        box-shadow: 0 0 10px #ddd;
    }
    .avater_box{
        height: 130px;
        width: 130px;
        border: 1px solid #eee;
        border-radius: 50%;
        padding: 10px;
        box-shadow: 0 0 10px #ddd;
        position: absolute;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: #fff;
        img{
            height: 100%;
            width: 100%;
            border-radius: 50%;
            background-color: #eee;
        }
    }
    .loginForm{
        position: absolute;
        bottom: 0;
        width: 100%;
        box-sizing: border-box;
        padding: 20px;
    }
    .btns{
        display: flex;
        justify-content: flex-end;
    }
</style>