<template>
  <div :class="{'cliente' : !isPremium, 'cliente-premium': isPremium}">
    <h4>Nome: {{ cliente.nome }}</h4>
    <hr>
    <p>Email: {{ cliente.email | processarEmail }}</p>
    <p v-if="showIdade">Idade: {{ cliente.idade }}</p>
    <p v-else>O usuário escondeu a idade!</p>
    <button @click="mudarCor($event)">Mudar cor!</button>
    <button @click="emitirEventoDelete">Deletar</button>
    <h4>Id especial: {{idEspecial}}</h4>
  </div>
</template>

<script>
export default {
  data(){
    return {
      isPremium: false,
    }
  },
  props: {
    cliente: Object,
    showIdade: Boolean
  },
  methods: {
    mudarCor: function($event){
      console.log($event);
      this.isPremium = !this.isPremium;
    },
    emitirEventoDelete: function(){
      this.$emit("deletando", {idDoCliente: this.cliente.id, curso: "formação node.js", emPromocao: true, component: this});
    },
  },
  filters:{
    processarEmail: function(value) {
      return value.toUpperCase();
    }
  },
  computed: {
    idEspecial: function(){
      return (this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
    }
  }
}
</script>

<style scoped>
  .cliente {
    background-color: #ECE5E3 ;
    max-width: 600px;
    height: 160px;
    padding: 1%;
    text-align: center;
    margin-top: 2%;
  }

  .cliente-premium{
    background-color: black ;
    color: blanchedalmond;
    max-width: 600px;
    height: 160px;
    padding: 1%;
    text-align: center;
    margin-top: 2%;
  }
</style>