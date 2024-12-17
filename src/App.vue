<template>
  <div id="app">
    <nav>
      <router-link to="/Login">登录</router-link> |
      <router-link to="/Register">注册</router-link> |
      <router-link to="/ForgetPassword">忘记密码</router-link> |
      <router-link to="/Home">首页</router-link> |
      <router-link to="/UserProfile">个人中心</router-link> |
      <router-link to="/Post">发帖</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style lang="less">
  body{
    margin: 0px;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100vh;
  background: #f5f5f5;
  margin: 0;
  padding: 0;
}

nav {
  padding: 20px 0;
  margin: 0;
  background: #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);

  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    padding: 5px 10px;
    margin: 0;
    border-radius: 4px;
    transition: all 0.3s ease;

    &:hover {
      background: #f0f0f0;
    }

    &.router-link-exact-active {
      color: #42b983;
      background: #e8f5e9;
    }
  }
}
</style>
