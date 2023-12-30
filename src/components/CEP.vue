<template>
  <v-main class="">
    <v-card class="mx-auto my-15 w-50 pa-10 effect-tr">
      <h1 class="text-center ">Digite o CEP desejado</h1>
      <v-form class="mt-10">
        <div class="d-flex">
            <v-text-field
              label="Digite seu CEP"
              v-model="address.cep"
              outlined
              class="w-50 mr-2"
            />
            <v-btn ripple size="55" rounded="1" color="transparent" @click="searchCEP">
                <v-icon>mdi-magnify</v-icon>
            </v-btn>
        </div>
        <v-text-field
          class="inputs"
          outlined
          label="Logradouro"
          v-model="address.logradouro"
        ></v-text-field>
        <v-text-field
          class="inputs"
          outlined
          label="Bairro"
          v-model="address.bairro"
        ></v-text-field>
        <v-text-field
          class="inputs"
          outlined
          label="Localidade"
          v-model="address.localidade"
        ></v-text-field>
        <v-text-field
          class="inputs"
          outlined
          label="UF"
          v-model="address.uf"
        ></v-text-field>
      </v-form>
    </v-card>
  </v-main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      address: {
        cep: null,
        logradouro: null,
        complemento: null,
        bairro: null,
        localidade: null,
        uf: null,
        pais: null,
      },
    };
  },
  methods: {
    searchCEP() {
      try {
        if(!this.address.cep){ 
            alert('Informe o CEP')
            throw new Error('Informe o CEP')}
        axios
          .get(`https://viacep.com.br/ws/${this.address.cep}/json/`)
          .then((response) => {
            this.address = response.data;
            console.log(this.address);
          });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>

h1 {
  font-size: 2rem;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.effect-tr{
    background-color: rgba(255, 255, 255, 0.904);
}

</style>
