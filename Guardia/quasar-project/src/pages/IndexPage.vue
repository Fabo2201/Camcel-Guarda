<template>
  <q-page >
    <q-list bordered >
      <q-item> 
         <q-item-section> <q-item-label header>Nombre Empresa</q-item-label></q-item-section> 
         <q-item-section> <q-item-label header>Trabajo a realizar</q-item-label></q-item-section>
         <q-item-section  class="flex-center"> <q-item-label header>Fecha</q-item-label></q-item-section>
         <q-item-section  class="flex-center"> <q-item-label header>Hora de Entrada</q-item-label></q-item-section>
         <q-item-section  class="flex-center"> <q-item-label header>Hora de Salida</q-item-label></q-item-section>
         <q-item-section  class="flex-center"> <q-item-label header>Confirmacion</q-item-label></q-item-section>

      </q-item>
      <q-item v-for="(actividad, index) in actividadesFiltradas" :key="index" :class="{'bg-grey-4': index % 2 === 0}">
       
       <q-item-section class="q-ml-lg"> 
        {{ actividad.nombre }} 
        </q-item-section> 

        <q-item-section> 
        {{ actividad.trabajo }}
        </q-item-section>

        <q-item-section class="flex-center"> 
        {{ actividad.fecha }}
        </q-item-section>

        <q-item-section  class="flex-center"> 
        {{ actividad.horaEntrada }}
        </q-item-section>

        <q-item-section  class="flex-center">  
        {{ actividad.horaSalida }}
        </q-item-section>

        <q-item-section  class="flex-center"> <q-checkbox 
            v-model="actividad.completada"
            @update:model-value="actualizarActividad(index, actividad.completada)"
          /></q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script setup>
import { ref, computed } from 'vue';

const actividades = ref([
    { nombre: "Los Pinos", trabajo: "Revisar sistema eléctrico", horaEntrada: "8:00", horaSalida: "17:00", fecha: "2024-08-23", completada: false },
  { nombre: "El Roble", trabajo: "Reparar sistema de agua", horaEntrada: "9:00", horaSalida: "18:00", fecha: "2024-08-24", completada: false },
  { nombre: "Industria Metalúrgica", trabajo: "Mantenimiento de máquinas", horaEntrada: "7:30", horaSalida: "16:00", fecha: "2024-08-25", completada: false },
  { nombre: "Colegio San Martín", trabajo: "Instalación de paneles solares", horaEntrada: "7:00", horaSalida: "15:00", fecha: "2024-08-26", completada: false },
  { nombre: "Hospital Central", trabajo: "Reparación de generador", horaEntrada: "6:30", horaSalida: "14:30", fecha: "2024-08-27", completada: false },
  { nombre: "Taller Mecánico López", trabajo: "Reemplazo de luces fluorescentes", horaEntrada: "10:00", horaSalida: "19:00", fecha: "2024-08-28", completada: false },
  { nombre: "Fábrica de Plásticos", trabajo: "Inspección de seguridad", horaEntrada: "8:30", horaSalida: "17:30", fecha: "2024-08-29", completada: false },
  { nombre: "Universidad Nacional", trabajo: "Revisión de red eléctrica", horaEntrada: "7:45", horaSalida: "16:15", fecha: "2024-08-30", completada: false },
  { nombre: "Estación de Bomberos", trabajo: "Mantenimiento de equipo", horaEntrada: "7:00", horaSalida: "15:30", fecha: "2024-08-31", completada: false },
  { nombre: "Centro Comercial Las Flores", trabajo: "Instalación de cámaras de seguridad", horaEntrada: "9:00", horaSalida: "18:00", fecha: "2024-09-01", completada: false }

  // Agrega más actividades aquí
]);

const actividadesFiltradas = computed(() => {
  const hoy = new Date().toISOString().split('T')[0]; // Obtiene la fecha actual en formato YYYY-MM-DD
  return actividades.value.filter(actividad => actividad.fecha >= hoy);
});
</script>
<style scoped>

  
</style>