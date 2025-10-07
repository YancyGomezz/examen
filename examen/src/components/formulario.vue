<template>
  <form @submit.prevent="registrar">
    <div>
      <label>Nombre:</label>
      <input v-model="nombre" @blur="validarNombre" placeholder="Nombre" />
      <span v-if="errores.nombre" class="error">{{ errores.nombre }}</span>
    </div>

    <div>
      <label>Dirección:</label>
      <input v-model="direccion" @blur="validarDireccion" placeholder="Dirección" />
      <span v-if="errores.direccion" class="error">{{ errores.direccion }}</span>
    </div>

    <div>
      <label>Edad:</label>
      <input v-model="edad" @blur="validarEdad" type="number" placeholder="Edad" />
      <span v-if="errores.edad" class="error">{{ errores.edad }}</span>
    </div>

    <button type="submit">Registrar</button>

    <p v-if="registroExitoso" class="exito">Usuario registrado con éxito</p>
  </form>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      direccion: '',
      edad: '',
      errores: {
        nombre: '',
        direccion: '',
        edad: ''
      },
      registroExitoso: false
    };
  },
  methods: {
    validarNombre() {
      const soloLetras = /^[A-Za-zÁÉÍÓÚÑáéíóúñ\s]+$/;
      if (!this.nombre) {
        this.errores.nombre = 'El nombre no puede estar vacío.';
      } else if (this.nombre.length < 2) {
        this.errores.nombre = 'El nombre debe tener al menos 2 caracteres.';
      } else if (!soloLetras.test(this.nombre)) {
        this.errores.nombre = 'El nombre debe contener solo letras.';
      } else {
        this.errores.nombre = '';
      }
    },
    validarDireccion() {
      const formatoDireccion = /^[A-Za-z0-9\s#\-,.]+$/;
      if (!this.direccion) {
        this.errores.direccion = 'La dirección no puede estar vacía.';
      } else if (this.direccion.length < 5) {
        this.errores.direccion = 'La dirección debe tener al menos 5 caracteres.';
      } else if (!formatoDireccion.test(this.direccion)) {
        this.errores.direccion = 'La dirección contiene caracteres inválidos.';
      } else {
        this.errores.direccion = '';
      }
    },
    validarEdad() {
      const edadNum = parseInt(this.edad);
      if (!this.edad) {
        this.errores.edad = 'La edad no puede estar vacía.';
      } else if (isNaN(edadNum)) {
        this.errores.edad = 'La edad debe ser un número.';
      } else if (edadNum < 0 || edadNum > 120) {
        this.errores.edad = 'La edad debe estar entre 0 y 120.';
      } else {
        this.errores.edad = '';
      }
    },
    registrar() {
      this.validarNombre();
      this.validarDireccion();
      this.validarEdad();

      if (!this.errores.nombre && !this.errores.direccion && !this.errores.edad) {
        console.log("Registrado:", this.nombre, this.direccion, this.edad);
        this.registroExitoso = true;
      } else {
        this.registroExitoso = false;
      }
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

input {
  padding: 8px;
  font-size: 1em;
}

button {
  padding: 10px;
  background-color: #2e8b57;
  color: white;
  border: none;
  cursor: pointer;
  font-weight: bold;
}

.error {
  color: red;
  font-size: 0.9em;
}

.exito {
  color: green;
  margin-top: 10px;
  font-weight: bold;
  text-align: center;
}

/* Centrar todo el contenido */
body,
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>

 en formulario