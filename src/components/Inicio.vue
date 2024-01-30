<template>
<div  class="d-flex justify-content-center">
  <div>
    <h2 class="mb-4">Registro</h2>

    <form @submit.prevent="submitForm" class="container mt-5">
      <div v-if="errors.length" class="alert alert-danger">
        <b>Por favor, corrija el(los) siguiente(s) error(es):</b>
        <ul>
          <li v-for="error in errors" :key="error">{{ error }}</li>
        </ul>
      </div>

      <div class="mb-3">
        <label for="firstName" class="form-label">Nombre:</label>
        <input id="firstName" v-model.trim="firstName" type="text" class="form-control">
      </div>

      <div class="mb-3">
        <label for="paternalLastName" class="form-label">Apellido Paterno:</label>
        <input id="paternalLastName" v-model.trim="paternalLastName" type="text" class="form-control">
      </div>

      <div class="mb-3">
        <label for="maternalLastName" class="form-label">Apellido Materno:</label>
        <input id="maternalLastName" v-model.trim="maternalLastName" type="text" class="form-control">
      </div>

      <div class="mb-3">
        <label for="postalCode" class="form-label">CP:</label>
        <input id="postalCode" v-model.number="postalCode" type="number" class="form-control" pattern="[0-9]*">
      </div>

      <div class="mb-3">
        <label for="street" class="form-label">Calle:</label>
        <input id="street" v-model.trim="street" type="text" class="form-control">
      </div>

      <div class="mb-3">
        <label for="number" class="form-label">Número:</label>
        <input id="number" v-model.number="number" type="number" class="form-control" pattern="[0-9]*">
      </div>

      <div class="mb-3">
        <label for="city" class="form-label">Ciudad:</label>
        <input id="city" v-model.trim="city" type="text" class="form-control">
      </div>

      <div class="mb-3">
        <label for="birthdate" class="form-label">Fecha de Nacimiento:</label>
        <input id="birthdate" v-model="birthdate" type="date" :max="maxDate" class="form-control">
      </div>

      <div class="mb-3">
        <label for="email" class="form-label">Correo Electrónico:</label>
        <input id="email" v-model.trim="email" type="email" class="form-control">
      </div>

      <div class="mb-3">
        <label for="phoneNumber" class="form-label">Número Telefónico:</label>
        <input id="phoneNumber" v-model.number="phoneNumber" type="tel" class="form-control" pattern="[0-9]*">
      </div>

      <div class="mb-3">
        <label for="photo" class="form-label">Fotografía (PNG):</label>
        <input id="photo" type="file" accept="image/png" @change="handleFileChange" class="form-control">
      </div>

      <button type="submit" class="btn btn-primary">Enviar</button>
    </form>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: '',
      paternalLastName: '',
      maternalLastName: '',
      postalCode: '',
      street: '',
      number: '',
      city: '',
      birthdate: '',
      email: '',
      phoneNumber: '',
      photo: null,
      errors: []
    };
  },
  computed: {
    maxDate() {
      const today = new Date();
      return today.toISOString().split('T')[0]; // Formato ISO para la fecha máxima
    }
  },
  methods: {
    submitForm() {
      this.errors = [];

      if (!this.firstName.trim()) {
        this.errors.push('El nombre es obligatorio.');
      }
      if (!this.paternalLastName.trim()) {
        this.errors.push('El apellido paterno es obligatorio.');
      }
      if (!this.postalCode.trim() || isNaN(parseInt(this.postalCode))) {
        this.errors.push('El CP es obligatorio y debe contener solo números.');
      }
      if (!this.street.trim()) {
        this.errors.push('La calle es obligatoria.');
      }
      if (!this.number.trim()) {
        this.errors.push('El número es obligatorio.');
      }
      if (!this.city.trim()) {
        this.errors.push('La ciudad es obligatoria.');
      }
      if (!this.birthdate) {
        this.errors.push('La fecha de nacimiento es obligatoria.');
      } else {
        const today = new Date();
        const minDate = new Date(today.getFullYear() - 18, today.getMonth(), today.getDate());
        if (new Date(this.birthdate) >= minDate) {
          this.errors.push('Debe ser mayor de 18 años.');
        }
      }
      if (!this.email.trim() || !this.validateEmail(this.email.trim())) {
        this.errors.push('El correo electrónico no es válido.');
      }
      if (!this.phoneNumber.trim() || isNaN(parseInt(this.phoneNumber)) || this.phoneNumber.length !== 10) {
        this.errors.push('El número telefónico es obligatorio y debe contener 10 dígitos numéricos.');
      }
      if (!this.photo) {
        this.errors.push('La fotografía es obligatoria.');
      }

      if (this.errors.length === 0) {
        // Aquí enviar el formulario, por ejemplo, enviar los datos a través de una solicitud HTTP
        console.log('Formulario enviado correctamente.');
      }
    },
    handleFileChange(event) {
      const file = event.target.files[0];
      if (file && file.type === 'image/png' && file.size <= 3 * 1024 * 1024) { // Menos de 3MB
        this.photo = file;
      } else {
        this.errors.push('La fotografía debe ser un archivo PNG y tener un tamaño menor a 3MB.');
      }
    },
    validateEmail(email) {
      // Expresión regular para validar el formato del correo electrónico
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    }
  }
};
</script>
