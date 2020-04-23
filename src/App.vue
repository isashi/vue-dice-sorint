<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.basic-button {
  color: #494949;
  text-transform: uppercase;
  text-decoration: none;
  background: #ffffff;
  padding: 10px;
  border: 4px solid #494949;
  display: inline-block;
  transition: all 0.4s ease 0s;
  margin: 0 5px;
  cursor: pointer;
}

.basic-button:hover {
  color: #ffffff;
  background: #f6b93b;
  border-color: #f6b93b;
  transition: all 0.4s ease 0s;
}
</style>
