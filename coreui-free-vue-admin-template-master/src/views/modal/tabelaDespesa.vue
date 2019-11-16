
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
                </tr>
              </thead>
              <tbody>
                <tr v-for="despesa in despesaNova" :key="despesa.descricao">
                  <td>
                    {{despesa.descricao}}
                  </td>
                  <td>
                    {{despesa.valor}}
                  </td>
                  <td>
                    {{despesa.data}}
                  </td>
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
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td></td>
                  <td></td>
                  <td></td>
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