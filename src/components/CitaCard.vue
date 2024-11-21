<template>
    <div :class="['cita-card', gravedadClase]">
      <p><strong>Paciente:</strong> {{ cita.paciente }}</p>
      <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
      <p><strong>Hora:</strong> {{ cita.hora }}</p>
      <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
      <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
      <button @click="eliminarCita">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    name: "CitaCard",
    props: ["cita"],
    computed: {
      gravedadClase() {
        return {
          Alta: "alta",
          Media: "media",
          Baja: "baja",
        }[this.cita.gravedad];
      },
    },
    methods: {
      eliminarCita() {
        this.$emit("eliminar-cita", this.cita);
      },
    },
  };
  </script>
  
  <style scoped>
  .cita-card {
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
    color: white;
  }
  .alta {
    background-color: red;
  }
  .media {
    background-color: yellow;
    color: black;
  }
  .baja {
    background-color: green;
  }
  button {
    margin-top: 10px;
  }
  </style>
  