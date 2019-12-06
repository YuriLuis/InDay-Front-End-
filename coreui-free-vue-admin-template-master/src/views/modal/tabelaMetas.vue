
<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="wrapper">
          <div class="animated fadeIn">
            <b-card-header>
              <strong>Meta</strong>
            </b-card-header>

            <table class="table table-hover table-success">
              <thead class="bg-warning">
                <tr>
                  <th scope="col">Descrição</th>
                  <th scope="col">Valor mensal</th>
                  <th scope="col">Data Inicio</th>
                  <th scope="col">Data Fim</th>
                  <th scope="col">Categoria</th>
                 
                </tr>
              </thead>
              <tbody>
                <tr v-for="meta in metas" :key="meta.descricao">
                  <td>{{meta.descricao}}</td>
                  <td>{{meta.valor}}</td>
                  <td>{{meta.datainicio}}</td>
                  <td>{{meta.datafim}}</td>
                  <td>{{meta.categoria}}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
        </div>
  </div>
</div>   
</template>
<script>
import axios from 'axios'
export default {
  props: {
    metaNova: {
      typer: Array
    },
  },
  name: "tabelaMeta",

  data() {
    return {
      metas: [],
     
    };
  },
  methods: {
    SalvarListaMetas() {},
    GetMetas(){
    axios
    .get("http://localhost:8080/meta")
    .then(response =>{
      this.metas = response.data
    })
  
  },
  
  watch: {
    metas: function(val) {
      this.GetMetas()
    }
  },
  mounted() {
    this.GetMetas();
   
  }
  },
}

</script>