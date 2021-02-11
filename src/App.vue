<template>
    <div id="app">
        <input type="text" v-model="clienteRaphael.nome">
        <Cliente :cliente="clienteRaphael" />
        <Cliente :cliente="clienteRaphael" />
        <Cliente :cliente="clienteRaphael" />
    </div>
</template>

<script>
import Cliente from './components/Cliente'
// import Produto from './components/Produto'

export default {
    name : 'App',
    data(){
        return{
            nomeDoRaphael: "Raphael Sartorio",
            clienteRaphael: {
                nome: "Raphael Sartorio",
                email: "raphaelsartorio9@gmail.com",
                idade: 22,
            }
        }
    },
    components: {
        Cliente,
        // Produto
    }
}
</script>