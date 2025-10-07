<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/formulario">formulario</router-link>
      <div id="app">
    <h1>Registro de Usuarios</h1>
    <FormularioRegistro />
  </div>
  </nav>
  <router-view/>
</template>


<script>
import FormularioRegistro from './components/formulario.vue';

export default {
  components: {
    FormularioRegistro
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>