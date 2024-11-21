<template>
  <div>
    <FormularioCita @nueva-cita="agregarCita" />
    <div v-if="citas.length === 0">Aún no hay consultas registradas</div>
    <div v-else>
      <CitaCard
        v-for="(cita, index) in citas"
        :key="index"
        :cita="cita"
        @eliminar-cita="eliminarCita"
      />
    </div>
  </div>
</template>

<script>
import FormularioCita from "./components/FormularioCita.vue";
import CitaCard from "./components/CitaCard.vue";

export default {
  name: "App",
  components: { FormularioCita, CitaCard },
  data() {
    return {
      citas: [],
    };
  },
  methods: {
    agregarCita(cita) {
      this.citas.push(cita);
    },
    eliminarCita(cita) {
      this.citas = this.citas.filter((c) => c !== cita);
    },
  },
};
</script>

