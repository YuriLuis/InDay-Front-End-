
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
                <tr v-for="despesa in despesaNova" :key="despesa.descricao">
                  <td>{{despesa.descricao}}</td>
                  <td>{{despesa.valor}}</td>
                  <td>{{despesa.data}}</td>
                  <td>Categoria</td>
                  <td>{{despesa.ehDespesaFixa}}</td>
                  <td>{{despesa.ehLancamentoParcelado}}</td>
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
                <tr v-for="receita in receitaNova" :key="receita.descricao">
                  <td>{{receita.descricao}}</td>
                  <td>{{receita.valor}}</td>
                  <td>{{receita.data}}</td>
                  <td>Categoria</td>
                  <td>{{receita.ehDespesaFixa}}</td>
                  <td>{{receita.ehLancamentoParcelado}}</td>
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
      despesas: []
    };
  },
  methods: {
    SalvarListaDespesas() {}
  },
  watch: {
    despesaNova: function(val) {}
  },
  mounted() {
    this.SalvarListaDespesas();
  }
};
</script>