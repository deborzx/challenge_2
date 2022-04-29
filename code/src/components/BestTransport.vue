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
      <div class="linha"></div>

      <p for="transports" class="type-two">Destino</p>
        <select class="campo" name="transports" id="transports" v-model="transports">
          <option value="">Selecione o destino do frete</option>
          <option v-for="transports in transport" :key="transports.id" :values="transports.name">{{ transports.name }}</option>
        </select>

      <p class="type-two">Peso</p>
        <input class="campo" type="number" v-model="rafa" placeholder="Insira aqui o peso da carga em Kg">
    </div>

    <div class="btn">      
    <button class="ajust">Analisar</button>
    </div>

    <div class="container best-alternatives">
      <p class="type-one">Estas são as melhores alternativas de frete que encontramos para você</p>
      <div class="linha"></div>
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
    // eslint-disable-next-line no-unused-vars
    async function getInfo(){
      const req = await fetch("http://localhost:3000/transport");
      const data = await req.json();

      this.id = data.id;
      this.name = data.name;
      this.cost_transport_light = data.cost_transport_light;
      this.cost_transport_heavy = data.cost_transport_heavy;
      this.city = data.city;
      this.lead_time = data.lead_time;
    }
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

.campo{
  background: #CFE2F3;
  width: calc(50%);
  height: calc(50px);
}

.linha{
  align: left;
  width: 50%;
  border-bottom: 1px solid #000000;
}

</style>
