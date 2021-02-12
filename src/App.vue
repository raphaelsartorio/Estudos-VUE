<template>
    <div id="app">
        <h3>Cadastro: </h3>
        <small id="nomeErro" v-show="deuErro">Por favor, preencha todos os campos!</small> <br>
        <input type="text" placeholder="nome" v-model="nomeField"> <br>
        <input type="email" placeholder="Email" v-model="emailField"> <br>
        <input type="number" placeholder="Idade" v-model="idadeField"> <br>
        <button @click="cadastrarUsuario">Cadastrar</button>
        <hr>
        <div v-for="(cliente,index) in clientes" :key="cliente.id">
            <h4>{{ index + 1}}</h4>
            <Cliente :cliente="cliente" @deletando="excluindoCliente($event)"/>
        </div>
    </div>
</template>

<script>
import Cliente from './components/Cliente'
// import Produto from './components/Produto'

export default {
    name : 'App',
    data(){
        return{
            nomeField: "",
            emailField: "",
            idadeField: 0,
            deuErro: false,
            clientes: [
                {
                    id: 2,
                    nome: "Raphael Sartorio",
                    email: "raphaelsartorio9@gmail.com",
                    idade: 22,
                },
                {
                    id: 1,
                    nome: "thiago da silva sauro",
                    email: "thiagoSauro@gmail.com",
                    idade: 8,
                },
                {
                    id: 3,
                    nome: "stephaniel da silva sauro",
                    email: "stephanielSauro@gmail.com",
                    idade: 22,
                },
            ]
        }
    },
    components: {
        Cliente,
        // Produto
    },
    methods: {
        cadastrarUsuario: function(){
            if(this.nomeField == "" || this.nomeField == " " || this.nomeField.lenght < 3){
                this.deuErro = true;
                return false;
            } 
            if(this.emailField == "" || this.emailField == "  "){
                this.deuErro = true;
                return false;
            }
            if(this.idadeField == 0){
                this.deuErro = true;
                return false;
            }
            else {
            this.clientes.push({nome: this.nomeField, email: this.emailField, idade: this.idadeField, id: Date.now()}),
            this.nomeField = "";
            this.emailField = "";
            this.idadeField = 0;
            this.deuErro = false;
            }
        },
        excluindoCliente: function($event){
            var id = $event.idDoCliente;
            var novoArray = this.clientes.filter(cliente => cliente.id != id);
            this.clientes = novoArray;
        }
    }
}
</script>

<style scoped>

    #nomeErro {
        color: red;
    }
</style>