<script setup>
import { reactive } from "vue";
const paciente = reactive({
  nombre: "",
  propietario: "",
  email: "",
  alta: "",
  sintomas: "",
});

const validar = () => {
  if (Object.values(paciente).includes("")) {
    console.log("Faltan campos");
    return;
  }
};
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Formulario</h2>

    <p class="text-lg mt-5 text-center mb-10">
      añade pacientes
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>
    <form
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
      @submit.prevent="validar"
    >
      <div mb-5>
        <label for="mascota" class="block text-gray-700 upercase font-bold">
          Nombre Mascota
        </label>
        <input
          id="mascota"
          type="text"
          placeholder="Nombre Mascota"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400"
          v-model="paciente.nombre"
        />
      </div>
      <div mb-5>
        <label for="propietario" class="block text-gray-700 upercase font-bold">
          Nombre propierario
        </label>
        <input
          id="propietario"
          type="text"
          placeholder="Nombre del propieratio"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400"
          v-model="paciente.propietario"
        />
      </div>
      <div mb-5>
        <label for="email" class="block text-gray-700 upercase font-bold">
          Email propierario
        </label>
        <input
          id="email"
          type="email"
          placeholder="Nombre del propieratio"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400"
          v-model="paciente.email"
        />
      </div>
      <div mb-5>
        <label for="alta" class="block text-gray-700 upercase font-bold">
          Alta
        </label>
        <input
          id="alta"
          type="date"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400"
          v-model="paciente.alta"
        />
      </div>
      <div mb-5>
        <label for="sintomas" class="block text-gray-700 upercase font-bold">
          Nombre propierario
        </label>
        <textarea
          id="sintomas"
          placeholder="Describe los sintomas"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          v-model="paciente.sintomas"
        />
      </div>
      <input
        type="submit"
        class="bg-indigo-600 p-3 text-white uppercase font-bold hover:bg-indigo w-full cursor-pointer transition-colors"
        value="Agregar paciente"
      />
    </form>
  </div>
</template>
