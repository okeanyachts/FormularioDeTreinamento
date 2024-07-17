<template>

<form>
  <div class="space-y-12">
    <div class="border-b border-gray-900/10 pb-12">
      <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
        <div class="sm:col-span-4">
          <label for="fullname" class="block text-lg font-medium leading-6 text-gray-900 ml-2">Nome Completo</label>
          <div class="mt-2">
            <input type="text" name="fullname" id="fullname" class="ml-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" placeholder="Seu nome completo">
          </div>
        </div>

        <div class="sm:col-span-4">
          <label for="sector" class="ml-2 block text-lg font-medium leading-6 text-gray-900">Setor</label>
          <div class="mt-2">
            <input type="text" name="sector" id="sector" class="ml-2 block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" placeholder="Seu setor">
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="mt-6 flex items-center justify-end gap-x-6 ">
    <button type="submit" class="rounded-md bg-indigo-600 px-3 py-2 mr-4 text-lg font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Enviar</button>
  </div>
</form>


</template>

<script>
export default {
  components: {
   
  },
  data() {
    return {
        algumacoisa: true 
    };
  },
  methods: {
    loginDoUsuario() {
        this.algumacoisa = false
    }
  },
};
</script>


