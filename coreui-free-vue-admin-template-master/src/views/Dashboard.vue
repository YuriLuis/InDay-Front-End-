<template>
  <div class="animated fadeIn">
    <b-row>
      <b-col sm="6" lg="3">
        <b-card no-body class="bg-primary">
          <b-card-body class="pb-0">
            <h4 class="mb-0">Saldo</h4>
            <h2 align="center">R$ {{saldo}}</h2>
            <p></p>
          </b-card-body>
          <card style="height:70px;" height="70" />
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "dashboard",
  components: {},
  data() {
    return {
      despesas: [],
      receitas: [],
      saldo: 0
    };
  },
  methods: {
    GerarSaldo() {
      axios
      .get("http://localhost:8080/despesa/saldo")
      .then(response => {
        this.saldo = response.data;
      });
     console.log(this.receitas.length)
    }
  },
 
  mounted(){
    this.GerarSaldo()
  }
 
};
</script>

<style>
/* IE fix */
#card-chart-01,
#card-chart-02 {
  width: 100% !important;
}
</style>
