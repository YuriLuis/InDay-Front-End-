
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
                <tr v-for="meta in metasNova" :key="meta.id">
                  <td>{{meta.descricao}}</td>
                  <td>{{meta.valorMensal}}</td>
                  <td>{{meta.dataInicio}}</td>
                  <td>{{meta.dataFim}}</td>
                  <td>{{meta.categoria?meta.categoria.descricao:"Não informada"}}</td>
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
// import axios from 'axios'
export default {
  props: {
    metasNova: {
      typer: Array
    },
  },
  name: "tabelaMeta",

  // // data() {
  //   return {
  //     metas: [],
     
  //   };
  // },
  // methods: {
  //   SalvarListaMetas() {},
  //   GetMetas(){
  //   console.log("erro");
  //   axios
  //   .get("http://localhost:8080/meta")
  //   .then(response =>{
  //     console.log("erro",response);
  //     this.metas = response.data
  //   })
  
  // },
  
  // watch: {
  //   metas: function(val) {
  //     this.GetMetas()
  //   }
  // },
  // mounted() {
  //   console.log("mouted")
  //   this.GetMetas();
   
  // }
  
}

</script>