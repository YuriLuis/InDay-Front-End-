<template>
  <div class="animated fadeIn">
    <b-row>
      <b-col sm="6" lg="12">
        <b-card no-body class="bg-primary">
          <b-card-body class="pb-8">
            <h4 class="mb-8">Saldo</h4>
            <h2 align="center">R$:3556,00</h2>
          </b-card-body>
          <card style="height:70px;" :height="70"/>
        </b-card>
      </b-col>
      
     
      <b-col sm="6" lg="3">
        <b-card no-body class="bg-danger">
          <b-card-body class="pb-0">
            <b-dropdown class="float-right" variant="transparent p-0" right>
              <template slot="button-content">
                <i class="icon-plus"></i>
              </template>
              <b-dropdown-item>Despesa</b-dropdown-item>
              <b-dropdown-item>Receita</b-dropdown-item>
              <b-dropdown-item>Metas</b-dropdown-item>
            </b-dropdown>
            <h4 class="mb-0">Atalho</h4>
            <p></p>
          </b-card-body>
          <card style="height:70px;" height="70"/>
        </b-card>
      </b-col>
    </b-row>

    
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'dashboard',
  components: {
   
  },
  data: function () {
    return {
     
      
      
    }
  },
  methods: {
   GetDespesas(){
      axios
      .get("http://localhost:8080/despesa")
      .then(response =>{
        this.despesas = response.data
      })
   }
  }
}
</script>

<style>
  /* IE fix */
  #card-chart-01, #card-chart-02 {
    width: 100% !important;
  }
</style>
