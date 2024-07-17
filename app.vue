<template>
  <div>
    <form class="max-w-lg mx-auto p-8 bg-white rounded-lg mt-10" @submit.prevent="saveData">
      <div class="space-y-8">
        <div class="border-b border-gray-200 pb-6">
          <h2 class="text-2xl font-semibold leading-7 text-gray-900 text-center">Formulário de Presença</h2>
          <div class="mt-6 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
            <div class="sm:col-span-6">
              <label for="fullname" class="block text-lg font-medium leading-6 text-gray-900">Nome Completo</label>
              <div class="mt-2">
                <input v-model="nomeCompleto" type="text" name="fullname" id="fullname" class="block w-full rounded-md border-0 py-3 px-4 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" placeholder="Seu Nome Completo">
              </div>
            </div>

            <div class="sm:col-span-6">
              <label for="sector" class="block text-lg font-medium leading-6 text-gray-900">Setor</label>
              <div class="mt-2">
                <input v-model="seuSetor" type="text" name="sector" id="sector" class="block w-full rounded-md border-0 py-3 px-4 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" placeholder="Seu Setor">
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="mt-6 flex items-center justify-end gap-x-6">
        <button type="submit" class="rounded-md bg-indigo-600 px-5 py-3 text-lg font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Enviar</button>
      </div>
    </form>

    <div v-if="showDialog" class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50">
      <div class="bg-white p-6 rounded-lg shadow-lg">
        <h3 class="text-xl font-semibold">Sua presença foi confirmada {{ savedName }}</h3>
        <p class="mt-2">Sua presença foi confirmada em nosso Treinamento do FlakeFlow. Obrigado!</p>
        <button @click="closeDialog" class="mt-4 rounded-md bg-indigo-600 px-4 py-2 text-white">OK</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      supabase: useSupabaseClient(),
      nomeCompleto: '',
      seuSetor: '',
      showDialog: false,
      savedName: '',
      loading: false,
    };
  },
  methods: {
    async saveData() {
      try {
        const { data, error } = await this.supabase
          .from('FlakeFlow')
          .insert([
            { NomeCompleto: this.nomeCompleto, Setor: this.seuSetor }
          ]);

        if (error) {
          throw error;
        }

        this.savedName = this.nomeCompleto;
        this.showDialog = true;
        this.nomeCompleto = '';
        this.seuSetor = '';
      } catch (error) {
        console.error("Erro ao salvar dados:", error.message);
      }
    },
    closeDialog() {
      this.showDialog = false;
    }
  },
};
</script>
