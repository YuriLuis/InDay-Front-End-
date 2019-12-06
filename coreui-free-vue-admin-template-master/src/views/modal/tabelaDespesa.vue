
<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="wrapper">
          <div class="animated fadeIn">
            <b-card-header>
              <strong>Despesa</strong>
            </b-card-header>

            <table class="table table-hover table-success">
              <thead class="bg-primary">
                <tr>
                  <th scope="col">Descrição</th>
                  <th scope="col">Valor</th>
                  <th scope="col">Data</th>
                  <th scope="col">Categoria</th>
                  <th scope="col">É fixa</th>
                  <th scope="col">É parcelado</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="despesa in despesas" :key="despesa.descricao">
                  <td>{{despesa.descricao}}</td>
                  <td>{{despesa.valor}}</td>
                  <td>{{despesa.date}}</td>
                  <td>{{despesa.categoria.descricao}}</td>
                  <td v-if="despesa.despesaFixa">Sim</td>
                  <td v-else>Não</td>
                  <td v-if="despesa.despesaUnica">Sim</td>
                  <td v-else>Não</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="wrapper">
          <div class="animated fadeIn">
            <b-card-header>
              <strong>Receita</strong>
            </b-card-header>
            <table class="table table-hover">
              <thead class="bg-success">
                <tr>
                  <th scope="col">Descrição</th>
                  <th scope="col">Valor</th>
                  <th scope="col">Data</th>
                  <th scope="col">Categoria</th>
                  <th scope="col">É fixa</th>
                  <th scope="col">É parcelado</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="receita in receitas" :key="receita.descricao">
                  <td>{{receita.descricao}}</td>
                  <td>{{receita.valor}}</td>
                  <td>{{receita.date}}</td>
                  <td>{{receita.categoria.descricao}}</td>
                  <td v-if="receita.receitaFixa" >Sim</td>
                  <td v-else>Não</td>
                  <td v-if="receita.receitaUnica">Sim</td>
                  <td v-else>Não</td>
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
    despesaNova: {
      typer: Array
    },
    receitaNova: {
      typer: Array
    }
  },
  name: "tabelaDespesa",

  data() {
    return {
      despesas: [],
      receitas:[],
      dataFormatada : ''
    };
  },
  methods: {
    SalvarListaDespesas() {},
    GetReceitas(){
    axios
    .get("http://localhost:8080/receita")
    .then(response =>{
      this.receitas = response.data
    })
    },
    GetDespesas(){
      axios
      .get("http://localhost:8080/despesa")
      .then(response =>{
        this.despesas = response.data
      })
    
      this.FormatarData(this.despesas.date)
    
    },
     FormatarData(data) {
      let dataSplit = new Date(data);
      this.despesas.Date = dataSplit.toLocaleDateString();
    },
  },
  
  watch: {
    despesaNova: function(val) {},
    despesas : function(val){
     this.GetDespesas()
    },
    receitas: function(val){
      this.GetReceitas()
    }
  },
  mounted() {
    this.GetReceitas();
    this.GetDespesas();
  }
};
</script>