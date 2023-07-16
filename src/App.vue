<script setup>
import { ref, reactive } from 'vue';
import { uid } from 'uid';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

const pacientes = ref([]);

const paciente = reactive({
  id: null,
  nombre: 'Firulais',
  propietario: 'Francisco',
  email: 'francisco@mail.com',
  alta: '08-08-2021',
  sintomas: 'tiene fiebre, no quiere comer',
});

const guardarPaciente = () => {
  if(paciente.id) {
    console.log('Edicion');
    const {id } = paciente;
    const i = pacientes.value.findIndex(pacienteState => pacienteState.id === id );
    console.log('postPac', i);
    pacientes.value[i] = {...paciente};


  } else {
    console.log('Nuevo');
    pacientes.value.push({
      ...paciente,
      id: uid(),
    });
  }

  Object.assign(paciente, {
    nombre: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: '',
    id: null,
  });
};

const actualizarPaciente = (id) => {
  console.log('actualizar paciente', id);
  const pacienteAEditar = pacientes.value.filter(paciente => paciente.id === id)[0];
  console.log(pacienteAEditar);
  Object.assign(paciente, pacienteAEditar);
};

</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Formulario
        v-model:nombre="paciente.nombre"
        v-model:propietario="paciente.propietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
        @guardar-paciente="guardarPaciente"
        :id="paciente.id"

      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">
          Administra tus pacientes
        </h3>
        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10">
            Información de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>
          <Paciente
            v-for="paciente in pacientes"
            :key="paciente.id"
            :paciente="paciente"
            @actualizar-paciente="actualizarPaciente"
          />
        </div>
        <p v-else class="mt-10 text-2xl text-center">No hay</p>
      </div>
    </div>
  </div>
</template>
