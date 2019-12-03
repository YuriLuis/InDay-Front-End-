<template>
  <div class="wrapper">
    <div class="animated fadeIn">
      <b-card no-body>
        <b-card-header>
          <strong>Lançamentos</strong>
        </b-card-header>

        <b-card-body>
          <b-row class="align-items-center mt-3">
            <b-col sm xs="12" class="text-center mt-3">
              <b-button
                type="button"
                variant="primary"
                @click="primaryModal = true"
                class="mr-1"
                size="lg"
              >Despesa</b-button>
            </b-col>
            <b-col sm xs="12" class="text-center mt-3">
              <b-button
                type="button"
                variant="success"
                @click="successModal = true"
                class="mr-1"
                size="lg"
              >Receita</b-button>
            </b-col>

            <!--/.col-->
          </b-row>
          <!--/.row-->
        </b-card-body>
      </b-card>
    </div>

    <b-modal
      title="Despesa"
      variant="primary"
      header-bg-variant="primary"
      content-class="border-primary"
      v-model="primaryModal"
      @ok="primaryModal = false"
    >
      <b-row>
        <b-col sm="12">
          <b-card>
            <div slot="header">
              <strong>Lançamento de despesas</strong>
              <small></small>
            </div>

            <b-form-group>
              <label for="descrição">
                <strong>Descrição</strong>
              </label>
              <b-form-input
                v-model="despesa.descricao"
                type="text"
                placeholder="Informe a descrição"
              ></b-form-input>
            </b-form-group>
            <b-row>
              <b-col sm="6">
                <b-form-group id="valor">
                  <label for="valor">
                    <strong>Valor</strong>
                  </label>
                  <b-input-group>
                    <b-input-group-prepend>
                      <b-input-group-text>
                        <i class="fa fa-brasil"></i>
                      </b-input-group-text>
                    </b-input-group-prepend>
                    <b-form-input v-model="despesa.valor" type="number" placeholder="R$ 0.00"></b-form-input>
                  </b-input-group>
                </b-form-group>
              </b-col>
              <b-col sm="6">
                <b-form-group>
                  <label for="data">
                    <strong>Data</strong>
                  </label>
                  <b-form-input v-model="despesa.data" type="date" id="data"></b-form-input>
                </b-form-group>
              </b-col>
            </b-row>

            <strong>
              <b-form-group label="Categoria" label-for="Categorias" :label-cols="3">
                <b-form-select
                  id="basicSelect"
                  :plain="true"
                  :options="['Categorias','Option 1', 'Option 2', 'Option 3']"
                  value="Categorias"
                ></b-form-select>
              </b-form-group>
            </strong>
            <b-form-group label-for="basicCheckboxes" :label-cols="0">
              <b-form-checkbox-group
                stacked
                id="basicCheckboxes"
                name="Checkboxes"
                :plain="true"
                :checked="[]"
              >
                <b-form-checkbox value="1" v-model="despesa.ehDespesaFixa">
                  <strong>é despesa fixa? (mensal)</strong>
                </b-form-checkbox>
                <b-form-checkbox value="2" v-model="despesa.ehLancamentoParcelado">
                  <strong>é um lançamento parcelado</strong>
                </b-form-checkbox>
              </b-form-checkbox-group>
            </b-form-group>
            <div class="form-actions">
              <b-row class="align-items-center mt-2">
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button
                    type="submit"
                    variant="success"
                    size="sm"
                    @click="SalvarDespesa(despesa)"
                  >Salvar</b-button>
                </b-col>
              </b-row>
            </div>
          </b-card>
        </b-col>
      </b-row>
    </b-modal>

    <b-modal
      title="Receita"
      variant="success"
      header-bg-variant="success"
      content-class="border-success"
      v-model="successModal"
      @ok="successModal = false"
      ok-variant="success"
    >
      <b-row>
        <b-col sm="12">
          <b-card>
            <div slot="header">
              <strong>Lançamento de Receita</strong>
              <small></small>
            </div>
            <b-form-group>
              <label for="descrição">
                <strong>Descrição</strong>
              </label>
              <b-form-input
                type="text"
                id="descrição"
                placeholder="Informe a descrição"
                v-model="receita.descricao"
              ></b-form-input>
            </b-form-group>
            <b-row>
              <b-col sm="6">
                <b-form-group id="valor">
                  <label for="valor">
                    <strong>Valor</strong>
                  </label>
                  <b-input-group>
                    <b-input-group-prepend>
                      <b-input-group-text>
                        <i class="fa fa-brasil"></i>
                      </b-input-group-text>
                    </b-input-group-prepend>
                    <b-form-input type="text" placeholder="R$ 0.00" v-model="receita.valor"></b-form-input>
                  </b-input-group>
                </b-form-group>
              </b-col>
              <b-col sm="6">
                <b-form-group>
                  <label for="data">
                    <strong>Data</strong>
                  </label>
                  <b-form-input type="date" id="data" v-model="receita.data"></b-form-input>
                </b-form-group>
              </b-col>
            </b-row>
            <strong>
              <div class="form-group">
              <label for="categorias">Categorias</label>
                <select class="form-control" v-for="categoria in categorias" :key="categoria.id" value="categoria" :v-model="receita.categoria.id">
                  <option> <strong>{{categoria}}</strong></option>
                </select>
              </div>
            </strong>
            <b-form-group label-for="basicCheckboxes" :label-cols="0">
              <b-form-checkbox-group
                stacked
                id="basicCheckboxes"
                name="Checkboxes"
                :plain="true"
                :checked="[]"
              >
                <b-form-checkbox value="1" v-model="receita.ehDespesaFixa">
                  <strong>é receita fixa? (mensal)</strong>
                </b-form-checkbox>
                <b-form-checkbox value="2" v-model="receita.ehLancamentoParcelado">
                  <strong>é um lançamento parcelado?</strong>
                </b-form-checkbox>
              </b-form-checkbox-group>
            </b-form-group>
            <div class="form-actions">
              <b-row class="align-items-center mt-2">
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button
                    type="submit"
                    variant="success"
                    size="sm"
                    @click="SalvarReceita(receita)"
                  >Salvar</b-button>
                </b-col>
              </b-row>
            </div>
          </b-card>
        </b-col>
      </b-row>
    </b-modal>
    <tabela-despesa :despesa-nova="despesas" :receita-nova="receitas"></tabela-despesa>
  </div>
</template>

<script>
import tabelaDespesa from "./tabelaDespesa";
import tabelaReceita from "./tabelaReceita";
import axios from "axios";

export default {
  components: {
    tabelaDespesa,
    tabelaReceita
  },
  data() {
    return {
      myModal: false,
      largeModal: false,
      smallModal: false,
      primaryModal: false,
      successModal: false,
      warningModal: false,
      dangerModal: false,
      infoModal: false,
      despesa: {
        descricao: "",
        valor: "",
        data: "",
        ehDespesaFixa: [],
        ehLancamentoParcelado: []
      },
      receita: {
        descricao:null,
        valor:null,
        data:'',
        ehDespesaFixa: [],
        ehLancamentoParcelado: [],
        categoria:{}

      },
      obj:{},
      despesas: [],
      receitas: [],
      categorias: []
    };
  },
  methods: {
    SalvarDespesa(despesa) {
      let objNulo = false;

      if (
        despesa.descricao == "" ||
        despesa.valor == "" ||
        despesa.data == ""
      ) {
        objNulo = true;
      }

      const ps = this.despesas.find(p => {
        return (
          p.descricao == this.despesa.descricao &&
          p.valor == this.despesa.valor &&
          p.data == this.despesa.data
        );
      });

      let despesaFixa = false;
      let lancamentoParcelado = false;

      if (this.despesa.ehDespesaFixa[0] != undefined) {
        despesaFixa = true;
      }

      if (this.despesa.ehLancamentoParcelado[1] != undefined) {
        lancamentoParcelado = true;
      }

      if (ps == null && !objNulo) {
        this.despesas.push({
          descricao: this.despesa.descricao,
          valor: this.despesa.valor,
          data: this.FormatarData(this.despesa.data),
          ehDespesaFixa: despesaFixa ? "Sim" : "Não",
          ehLancamentoParcelado: lancamentoParcelado ? "Sim" : "Não"
        });
      }

      this.LimparCamposModalDespesa();
    },
    LimparCamposModalDespesa() {
      (this.despesa.descricao = ""),
        (this.despesa.valor = ""),
        (this.despesa.data = ""),
        (this.despesa.ehDespesaFixa = false),
        (this.despesa.ehLancamentoParcelado = false);
    },
    FormatarData(data) {
      let dataSplit = new Date(data);
      return dataSplit.toLocaleDateString();
    },
    SalvarReceita(receita) {
      let despesaFixa = false;
      let lancamentoParcelado = false;

      if (this.receita.ehDespesaFixa[0] != undefined) {
        despesaFixa = true;
      }
      if (this.receita.ehLancamentoParcelado[0] != undefined) {
        lancamentoParcelado = true;
      }

       this.obj= {
        descricao: this.receita.descricao,
        valor: this.receita.valor,
        date: this.receita.data,
        categoria:{
          id: 1
        } ,
        login:{
          id:12
        },
       
        despesaFixa: despesaFixa,
        despesaUnica: lancamentoParcelado,
        pago: true
      };
       this.PostReceita(this.obj)

      this.LimparCamposModaReceita();
    },
    LimparCamposModaReceita() {
      (this.receita.descricao = ""),
        (this.receita.valor = ""),
        (this.receita.data = ""),
        (this.receita.ehDespesaFixa = false),
        (this.receita.ehLancamentoParcelado = false);
    },
    PostReceita(obj) {
      axios.post("http://localhost:8080/receita", this.obj).then(response => {
        this.obj = response.data;
      });
    },
    GetCategorias() {
      axios
      .get("http://localhost:8080/categoria")
      .then(response => {
       this.categorias.push(response.data)
      });
    }
  },
   created: function () {
    // this.GetCategorias();
  },
    mounted() {
      this.GetCategorias();
    }
  
};
</script>

<style>
#valor {
  text-align: center;
}
</style>
