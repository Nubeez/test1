<template>
  <nav>
    <div class="menu"><router-link to="/">Home</router-link> | <router-link to="/product">Product</router-link> | <router-link to="/about">About</router-link></div>
  </nav>
  <router-view />
</template>

<style>
* {
  box-sizing: border-box;
  text-decoration: none;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav a {
  font-weight: bold;
  color: #fff;
  padding-left: 20px;
}

nav .menu {
  display: flex;
  justify-content: flex-start;
  background: navy;
  border-radius: 5px;
  line-height: 50px;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
