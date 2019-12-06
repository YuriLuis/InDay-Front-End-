<template>
  <div class="wrapper">
    <div class="animated fadeIn">
      <b-card no-body>
        <b-card-header>
          <strong>Categoria</strong>
        </b-card-header>
        <b-card-body>
          <b-row class="align-items-center mt-3">
            <b-col sm xs="12" class="text-center mt-3">
              <b-button
                type="button"
                variant="success"
                @click="warningModal = true"
                class="mr-1"
                size="lg"
              >Categoria</b-button>
            </b-col>

            <!--/.col-->
          </b-row>
          <!--/.row-->
        </b-card-body>
      </b-card>
    </div>

    <b-modal
      title="Categoria"
      variant="warning"
      header-bg-variant="success"
      content-class="border-warning"
      v-model="warningModal"
      @ok="warningModal = false"
      ok-variant="warning"
    >
      <b-row>
        <b-col sm="12">
          <b-card>
            <div slot="header">
              <strong>Descrição Da Categoria</strong>
              <small></small>
            </div>
            <b-form-group>
              <label for="descrição" te>
                <strong>Descrição</strong>
              </label>
              <b-form-input
                type="text"
                id="descrição"
                placeholder="Informe a descrição"
                v-model="categoria.descricao"
              ></b-form-input>
            </b-form-group>
            <b-col sm xs="12" class="text-center mt-5">
              <b-button type="submit" variant="success" size="sm" @click="SalvarDescricao()">Salvar</b-button>
            </b-col>
          </b-card>
        </b-col>
      </b-row>
    </b-modal>
    <tabela-categoria></tabela-categoria>
  </div>
</template>

<script>
import tabelaCategoria from "./tabelaCategoria";
import axios from "axios";

export default {
  components: {
    tabelaCategoria
  },
  name: "Despesa",
  data() {
    return {
      categoria: {
        descricao: ""
      },
      myModal: false,
      largeModal: false,
      smallModal: false,
      primaryModal: false,
      successModal: false,
      warningModal: false,
      dangerModal: false,
      infoModal: false
    };
  },
  methods: {
    SalvarDescricao() {
      
      console.log(this.categoria)
      axios.post("http://localhost:8080/categoria", this.categoria).then(response => {
        this.categoria = response.data
      });
    }
  }
};
</script>

<style>
#valor {
  text-align: center;
}
</style>
