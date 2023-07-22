<template>
    <main class="fatherInputs">
        <h1>Busca de CEP</h1>
        <form >
            <v-text-field label="Digite seu CEP" v-model="adress.cep" 
            outlined
            clearable
            required
            style="width: 300px;
            
               "/>
            <v-btn class="buttonSearchCEP" @click="searchCEP"><v-icon>mdi-magnify</v-icon></v-btn>
        </form>
        <div class="fatherInputs">
            <v-text-field class="inputs" outlined label="Logradouro" v-model="adress.logradouro"></v-text-field>
            <v-text-field class="inputs" outlined label="Bairro" v-model="adress.bairro"></v-text-field>
            <v-text-field class="inputs" outlined label="Localidade" v-model="adress.localidade"></v-text-field>
            <v-text-field class="inputs" outlined label="UF" v-model="adress.uf"></v-text-field>
        </div>
    </main>
</template>

<script>
    import axios from 'axios'
    export default{
        data(){
            return{
            adress: {
                cep: '',
                logradouro: '',
                complemento: '',
                bairro: '',
                localidade: '',
                uf: '',
                pais: ''
            }}
        },
        methods:{
            searchCEP(){
                
                try{
                    axios
                    .get(`https://viacep.com.br/ws/${this.adress.cep}/json/`)
                    .then(response => {
                        this.adress = response.data
                    })

                }catch(error){
                    console.log(error)
                }
            }
        }
    }
</script>

<style>

h1{
    font-size: 2rem;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.buttonSearchCEP{
    background-color: blueviolet;
    color: white;
}
.inputs{
    width: 50%;
}

form{
    display: flex;
    flex-direction: row;
}
.fatherInputs{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    width: 100%;
}
</style>

