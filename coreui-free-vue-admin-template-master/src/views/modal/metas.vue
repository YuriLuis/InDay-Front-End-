<template>
  <div class="wrapper">
    <div class="animated fadeIn">
      <b-card no-body>
        <b-card-header>
          <strong>Metas</strong>
        </b-card-header>

        <b-card-body>
          <b-row class="align-items-center mt-3">
            <b-col sm xs="12" class="text-center mt-3">
              <b-button
                type="button"
                variant="warning"
                @click="primaryModal = true"
                class="mr-1"
                size="lg"
              >Metas</b-button>
            </b-col>
           
            <!--/.col-->
          </b-row>
          <!--/.row-->
        </b-card-body>
      </b-card>
    </div>

    <tabela-metas :metasNova="metas"></tabela-metas> 
    

    <b-modal
      title="Metas"
      variant="primary"
      header-bg-variant="primary"
      content-class="border-primary"
      v-model="primaryModal"
      @ok="primaryModal = false" 
      ok-title="Sair"
      cancel-disabled
      no-close-on-esc
      no-close-on-backdrop
    >
      <b-row>
        <b-col sm="12">
          <b-card>
            <div slot="header">
              <strong>Lançamento de metas</strong>
              <small></small>
            </div>
meta {{meta}}
            <b-form-group>
              <label for="descrição"> <strong>Descrição</strong></label>
              <b-form-input type="text" id="descrição"  v-model="meta.descricao" placeholder="Informe a descrição"></b-form-input>
            </b-form-group>
            <b-row>
              <b-col sm="6">
                <b-form-group>
                  <label for="Data Inicio"><strong>Data Inicio</strong></label>
                  <b-form-input type="date" v-model="meta.dataInicio" id="data"></b-form-input>
                </b-form-group>
              </b-col>
              <b-col sm="6">
                <b-form-group>
                  <label for="Data Fim"><strong>Data Fim</strong></label>
                  <b-form-input type="date" v-model="meta.dataFim" id="data"></b-form-input>
                </b-form-group>
              </b-col>
            </b-row>

            <b-col sm="12">
              <b-form-group id="valor">
                <label for="valor"><strong> Valor Mensal </strong></label>
                <b-input-group>
                  <b-input-group-prepend>
                    <b-input-group-text>
                      <i class="fa fa-brasil"></i>
                    </b-input-group-text>
                  </b-input-group-prepend>
                  <b-form-input type="text" v-model="meta.valorMensal" placeholder="R$ 0.00"></b-form-input>
                </b-input-group>
              </b-form-group>
            </b-col>
             
            <div class="form-group">
              <label for="categorias">Categorias</label>
                <select class="form-control" v-model="meta.categoria"  >
                  <option v-for="categoria in categorias" 
                          :key="categoria.id"
                          :value="categoria"> <strong>{{categoria.descricao}}</strong>
                  </option>
                </select>
              </div>
            <div class="form-actions">
              <b-row class="align-items-center mt-2">
                <b-col sm xs="12" class="text-center mt-2">
                <b-button type="submit" variant="success" size="sm" @click="salvarMetas()">Salvar</b-button>                </b-col>
                <b-col sm xs="12" class="text-center mt-2">
                </b-col>
              </b-row>
            </div>
          </b-card>
        </b-col>
      </b-row>
    </b-modal>
  </div>
</template>

<script>
import tabelaMetas from "./tabelaMetas";
import categoria from "./categoria";
import axios from 'axios'

export default {
  name: "Metas",
  components: {
    tabelaMetas,
  },
  data: function () {
    return {
      myModal: false,
      largeModal: false,
      smallModal: false,
      primaryModal: false,
      successModal: false,
      warningModal: false,
      dangerModal: false,
      infoModal: false,
      meta: {
        descricao: "teste01",
        dataInicio: "",
        dataFim: "",
        valorMensal: "",
        categoria: "",
      },
      obj:{},
      metas: [], 
      categorias:[]
    };

},
methods: {
  salvarMetas() {
    console.log("salvar meta",this.meta)
    // let objNulo = false
    let self = this;

    axios.post("/meta",this.meta).then(response => {
      console.log("response post",response)
      self.LimparCamposMetas();
      self.GetMetas();
      self.primaryModal = false;
    //   //  this.meta =    response.data
    });
      
  },
  LimparCamposMetas() {
        this.meta.descricao = "";
        this.meta.dataInicio = "";
        this.meta.dataFim = "";
        this.meta.valorMensal = "";
        this.meta.categoria = "";    
  },
    
    // PostMetas(obj) {
    //   axios.post("http://localhost:8080/meta", this.obj).then(response => {
    //     this.obj = response.data;
    //   });
    // },
    GetMetas() {
      console.log("metas get metas")
      axios
      .get("http://localhost:8080/meta")
      .then(response => {
        console.log("metas get metas",response)
       this.metas = response.data
      });
    },
     GetCategorias() {
      axios
      .get("http://localhost:8080/categoria")
      .then(response => {
       this.categorias = response.data
      });
    }
  },
  //  created: function () {
  //    console.log("metas created")
  //   this.GetMetas();
  // },
    mounted() {
      console.log("metas mouted")
      this.GetMetas();
      this.GetCategorias();
    }
  
};
</script>

<style>
#valor {
  text-align: center;
}
</style>
