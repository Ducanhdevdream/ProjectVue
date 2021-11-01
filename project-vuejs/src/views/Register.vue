<template>
  <div class="loginWrap">
    <div class="logo">
      <img src="../assets/image/zent_logo_dark.png" alt="">
    </div>
    <el-form :model="ruleForm" :label-position="label" :rules="rules" ref="ruleForm" label-width="120px" class="demo-ruleForm">
      <el-form-item prop="email">
        <label style="float: left; line-height:30px">Email</label>
        <el-input v-model="ruleForm.email"></el-input>
      </el-form-item>
      <el-form-item prop="name">
        <label style="float: left; line-height:30px">Họ tên</label>
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item prop="password">
        <label style="float: left; line-height:30px">Mật khẩu</label>
        <el-input type="password" v-model="ruleForm.password"></el-input>
      </el-form-item>
      <el-form-item prop="checkPass">
        <label style="float: left; line-height:30px">Xác nhận mật khẩu</label>
        <el-input type="password" v-model="ruleForm.checkPass"></el-input>
      </el-form-item>
    </el-form>
    <button class="btn-login" @click="handleRegister('ruleForm')">
      ĐĂNG KÝ
    </button>
    <div class="register el-icon-back">
      <el-button style="color:black" @click="login()">Đăng nhập</el-button>
    </div>
  </div>
</template>

<script>


export default {
  name: "LoginForm",
  data() {
    
    return {
      ruleForm: {
        email: '',
        password: '',
        checkPass: '',
        name: '',
      },
      rules: {
        email: [
          { required: true, message: 'Email không được bỏ trống!', trigger: 'change' },
          { type: 'email', message: 'Email không hợp lệ!', trigger: 'blur' },
        ],
        password: [
          { required: true, message: 'Mật khẩu không được bỏ trống!', trigger: 'change' },
          { min: 6, message: 'Mật khẩu không được ít hơn 6 kí tự', trigger: 'blur' },
        ],
        name: [
          { required: true, message: 'Tên người dùng không được bỏ trống', trigger: 'change' },
        ],
        checkPass: [
          { validator: confirm, trigger: 'blur' }
        ],
      },
      label: 'top',
    }
  },
  methods: {
    forgotPass() {
      this.$router.push('forgot-password')
    },
    
    login() {
      this.$router.push('/path/login')
    }
  }
}
</script>

<style lang="scss" scoped>
.loginWrap {
  width: 420px;
  padding: 25px;
  background-color: white;
  border-radius: 25px;
  box-sizing: border-box;

  .logo {
    width: 100%;

    img {
      width: 180px;
    }
  }

  .inputWrap {
    width: 100%;
    height: auto;
    overflow: hidden;
    
    .el-input {
      height: 50px !important;
    }

    .error {
      font-size: 12px;
      color: #f54b5e;
      float: left;
    }
  }

  .register {
    margin-top: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    
    .el-button {
      border: 0;
      color: #0080dd;
      padding: 7px;
    }
  }

  .btn-login {
    margin-top: 20px;
    color: white;
    width: 100%;
    height: 36px;
    border: none;
    background: #42b72a;
    border-radius: 25px;
    font-size: 16px;
    box-sizing: border-box;
    outline: none;
    cursor: pointer;
  }
}
</style>