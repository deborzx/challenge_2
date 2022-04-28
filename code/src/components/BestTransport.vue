<template>
  <div class="title">
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand class="ml-2">
        <img class="img" src="./../assets/logo.png" width="50px">
        <b>{{ appName }}</b>
      </b-navbar-brand>
    </b-navbar>

    <div class="container">
      <p class="type-one">Como é o frete que voce precisa?</p>
      <hr align = "left" width="50%"/>

      <p class="type-two">Destino</p>
        <select v-model="selected">
          <option disabled value="">Escolha um item</option>
          <option>Expresso Oriente</option>
          <option>LevoJa</option>
          <option>Rapido Jacutinga</option>
        </select>

      <p class="type-two">Peso</p>
        <input type="number" v-model="rafa" placeholder="Insira aqui o peso da carga em Kg">
    </div>

    <div class="btn">      
    <button class="ajust">Analisar</button>
    </div>

    <div class="container best-alternatives">
      <p class="type-one">Estas são as melhores alternativas de frete que encontramos para você</p>
      <hr align = "left" width="50%"/>
    </div>
  </div>
</template>



<script>
import {
  BNavbar,
  BNavbarBrand,
} from 'bootstrap-vue'

export default {
  components: {
    BNavbar,
    BNavbarBrand,
  },
  data() {
    const appName = ''

    return {
      appName,
    }
  },
  created() {
    // Implemente aqui o GET dos dados da API REST
    // para que isso ocorra na inicialização da pagina
    this.appName = 'MELHOR FRETE'
  },
  methods: {
    // Implemente aqui os metodos utilizados na pagina
    methodFoo() {
      console.log(this.appName)
    },
  },
}
</script>

<style scoped>
.title .navbar {
  background-color: #93C47D !important;
}

.img{
  margin-right: 20px;
}

.title .navbar-brand {
  margin-left: 20px;
}

.container{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.type-one{
  margin-top: 24px;
  font-size: 16px;
  font-weight: bold;
}

.btn{
  display: flex;
  justify-content: center;
}

.ajust{
  align: center;
  margin-top: 24px;
  background: #92C47D;
  font-family: arial;
  font-weight: bold;
  border: solid 2px;
  border-radius: 6px;
  width: 130px;
  height: 41px;

}

.type-two{
  margin-top: 24px;
  font-size: 24px;
}

.best-alternatives{
  margin-top: 24px;
}

</style>
