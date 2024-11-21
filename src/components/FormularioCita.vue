<template>
    <div>
      <form @submit.prevent="agregarCita">
        <div class="form-group">
          <label :for="'paciente'" :style="{ color: cita.paciente ? 'black' : 'red' }">
            Paciente: 
          </label>
          <input
            id="paciente"
            v-model="cita.paciente"
            type="text"
            placeholder="Ingrese paciente"
          />
        </div>
  
        <div class="form-group">
          <label :for="'fecha'" :style="{ color: cita.fecha ? 'black' : 'red' }">
            Fecha: 
          </label>
          <input id="fecha" v-model="cita.fecha" type="date" />
        </div>
  
        <div class="form-group">
          <label :for="'hora'" :style="{ color: cita.hora ? 'black' : 'red' }">
            Hora: 
          </label>
          <input id="hora" v-model="cita.hora" type="time" />
        </div>
  
        <div class="form-group">
          <label :for="'gravedad'" :style="{ color: cita.gravedad ? 'black' : 'red' }">
            Gravedad: 
          </label>
          <select id="gravedad" v-model="cita.gravedad">
            <option value="" disabled>Seleccione una gravedad</option>
            <option value="Alta">Alta</option>
            <option value="Media">Media</option>
            <option value="Baja">Baja</option>
          </select>
        </div>
  
        <div class="form-group">
          <label :for="'motivo'" :style="{ color: cita.motivo ? 'black' : 'red' }">
            Motivo: 
          </label>
          <input
            id="motivo"
            v-model="cita.motivo"
            type="text"
            placeholder="Ingrese motivo"
          />
        </div>
  
        <button :disabled="!formularioValido" type="submit">
          Agregar
        </button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: "FormularioCita",
    data() {
      return {
        fields: ["paciente", "fecha", "hora", "gravedad", "motivo"],
        cita: {
          paciente: "",
          fecha: "",
          hora: "",
          gravedad: "",
          motivo: "",
        },
      };
    },
    computed: {
      formularioValido() {
        return this.fields.every((field) => this.cita[field]);
      },
    },
    methods: {
      agregarCita() {
        this.$emit("nueva-cita", { ...this.cita });
        this.resetFormulario();
      },
      resetFormulario() {
        this.fields.forEach((field) => (this.cita[field] = ""));
      },
    },
  };
  </script>
  
  <style scoped>
  .form-group {
    margin-bottom: 15px;
  }
  
  form input,
  form select,
  form button {
    display: block;
    margin-top: 5px;
    padding: 8px;
    font-size: 14px;
    width: 100%;
  }
  
  button {
    margin-top: 10px;
    padding: 10px 20px;
    cursor: pointer;
  }
  
  button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  </style>
  