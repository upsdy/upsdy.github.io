<template>
  <div class="login">
    <div class="login-bg">
      <div class="iconfont"></div>
    </div>
    <div class="login-input">
      <div class="user">
        <span>账号：</span>
        <span>
          <input class="mm" type="text" v-model="phone"/>
        </span>
      </div>
      <div  class="password">
        <span>密码：</span>
        <span>
          <input class="mm" type="password" v-model="password"/>
        </span>
      </div>
      <div class="btn">
        <span>

          <button @click="login">登录</button>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
     data:function(){
           return{
                phone:null,
                password:null,
           }
    },
    methods:{
        login(){
            this.axios(`http://apis.netstart.cn/music/login/cellphone?phone=${this.phone}&password=${this.password}`).then(data=>{
                console.log(data.data);
                localStorage.setItem('token',data.data.cookie);
                localStorage.setItem('id',data.data.account.id)
                this.$router.push('/');
            })
        },
    }
};
</script>

<style lang="less">
.iconfont{
  background:url("../assets/sytp.jpg") no-repeat;
  background-position:center; 
  background-size: contain;
}
.login {
  background-color: #DA0000;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 6;
  .login-bg {
    .iconfont {
      color: #fff;
      font-size: 110px;
      width: 110px;
      height: 110px;
      margin: 0 auto;
      margin-top: 100px;
    }
  }
  .login-input {
    width: 262px;
    margin: 0 auto;
    margin-top: 50px;
    .user {
      margin-bottom: 10px;
    }
    input {
      line-height: 24px;
      background-color:#DA0000;
      border-bottom: 2px solid #fff;
    }
    span {
      color: #fff;
    }
  }
  .mm{
     width: 100%;
    height: 30px;
    line-height: 18px;
    background: rgba(0, 0, 0, 0);
    font-size: 14px;
    color: #333;
    border: 0;
    outline: 0;
    line-height: 30px;
  }
  .btn {
    margin-top: 50px;
    display: flex;
    align-items: center;
    span {
      margin: 0 auto;
      display: inline-block;
      color: red;
      button {
        width: 70px;
        border-radius: 8px;
        line-height: 30px;
        background-color: #f00d0d;
        border: none;
        color: white;
      }
    }
  }
}
</style>