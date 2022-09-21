<script>
import axios from "axios";

  export default {
    data() {
      return {
        cep: "",
        endereco: {},
      };
    },
    methods: {
      async buscar(){
        const url = `https://viacep.com.br/ws/${this.cep}/json`;
        const res = await axios.get(url);
        this.endereco = res.data;
      }
    }
  }
</script>
<template>
  <div class="wrapper">
    <form @submit.prevent="buscar">
      <input type="text" v-model="cep" class="InputCep" placeholder="CEP:">
      <button type="submit" class="BtnCep">Procurar</button>
    </form>
    <br>
    <div class="end">
      <p>Rua: {{endereco.logradouro}}</p> 
      <p>Número: {{endereco.numero}}</p>
      <p>Bairro: {{endereco.bairro}}</p>
      <p>Cidade: {{endereco.localidade}}</p>
      <p>Complemento: {{endereco.logradouro}}</p>
      <p>Estado: {{endereco.uf}}</p>
      <p>DDD: {{endereco.ddd}}</p>
      <p>IBGE: {{endereco.ibge}}</p>
      <p>SIAFI: {{endereco.siafi}}</p>
    </div>
  </div>
</template>

<style>
  .end{
    background-color: antiquewhite;
    padding: 1vh ;
  } 
  .InputCep{
    width: 70%;
  }
  .BtnCep{
    width: 30%;
  }
  
</style>