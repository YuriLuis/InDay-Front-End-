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
            <b-col sm xs="12" class="text-center mt-3">
              <b-button
                type="button"
                variant="warning"
                @click="warningModal = true"
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
              <label for="descrição"><strong>Descrição</strong></label>
              <b-form-input type="text" id="descrição" placeholder="Informe a descrição"></b-form-input>
            </b-form-group>
            <b-row>
              <b-col sm="6">
                <b-form-group id="valor">
                  <label for="valor"><strong>Valor</strong></label>
                  <b-input-group>
                    <b-input-group-prepend>
                      <b-input-group-text>
                        <i class="fa fa-brasil"></i>
                      </b-input-group-text>
                    </b-input-group-prepend>
                    <b-form-input type="text" placeholder="R$ 0.00"></b-form-input>
                  </b-input-group>
                </b-form-group>
              </b-col>
              <b-col sm="6">
                <b-form-group>
                  <label for="data"><strong>Data</strong></label>
                  <b-form-input type="date" id="data"></b-form-input>
                </b-form-group>
              </b-col>
            </b-row>

            <strong> 
            <b-form-group  label="Categoria" label-for="Categorias" :label-cols="3">
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
                <b-form-checkbox value="1"> <strong>é despesa fixa? (mensal) </strong></b-form-checkbox>
                <b-form-checkbox value="2"> <strong>é um lançamento parcelado</strong></b-form-checkbox>
              </b-form-checkbox-group>
            </b-form-group>
            <div class="form-actions">
              <b-row class="align-items-center mt-2">
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button type="submit" variant="success" size="sm">Salvar</b-button>
                </b-col>
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button type="button" variant="danger" size="sm">Cancelar</b-button>
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
              <label for="descrição"><strong>Descrição</strong></label>
              <b-form-input type="text" id="descrição" placeholder="Informe a descrição"></b-form-input>
            </b-form-group>
            <b-row>
              <b-col sm="6">
                <b-form-group id="valor">
                  <label for="valor"><strong>Valor</strong></label>
                  <b-input-group>
                    <b-input-group-prepend>
                      <b-input-group-text>
                        <i class="fa fa-brasil"></i>
                      </b-input-group-text>
                    </b-input-group-prepend>
                    <b-form-input type="text" placeholder="R$ 0.00"></b-form-input>
                  </b-input-group>
                </b-form-group>
              </b-col>
              <b-col sm="6">
                <b-form-group>
                  <label for="data"><strong>Data</strong></label>
                  <b-form-input type="date" id="data"></b-form-input>
                </b-form-group>
              </b-col>
            </b-row>

            <strong> 
            <b-form-group  label="Categoria" label-for="Categorias" :label-cols="3">
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
                <b-form-checkbox value="1"> <strong>é receita fixa? (mensal) </strong></b-form-checkbox>
                <b-form-checkbox value="2"> <strong>é um lançamento parcelado?</strong></b-form-checkbox>
              </b-form-checkbox-group>
            </b-form-group>
            <div class="form-actions">
              <b-row class="align-items-center mt-2">
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button type="submit" variant="success" size="sm">Salvar</b-button>
                </b-col>
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button type="button" variant="danger" size="sm">Cancelar</b-button>
                </b-col>
              </b-row>
            </div>
          </b-card>
        </b-col>
      </b-row>
    </b-modal>
    <b-modal
      title="Metas"
      variant="warning"
      header-bg-variant="warning"
      content-class="border-warning"
      v-model="warningModal"
      @ok="warningModal = false"
      ok-variant="warning"
    >
      <b-row>
        <b-col sm="12">
          <b-card>
            <div slot="header">
              <strong>Lançamento de metas</strong>
              <small></small>
            </div>
            <b-form-group>
              <label for="descrição" te> <strong>Descrição</strong></label>
              <b-form-input type="text" id="descrição" placeholder="Informe a descrição"></b-form-input>
            </b-form-group>
            <b-row>
              <b-col sm="6">
                <b-form-group>
                  <label for="de"><strong>De</strong></label>
                  <b-form-input type="Date" id="de"></b-form-input>
                </b-form-group>
              </b-col>
              <b-col sm="6">
                <b-form-group>
                  <label for="data"><strong>Até</strong></label>
                  <b-form-input type="date" id="data"></b-form-input>
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
                  <b-form-input type="text" placeholder="R$ 0.00"></b-form-input>
                </b-input-group>
              </b-form-group>
            </b-col>
             
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
            <div class="form-actions">
              <b-row class="align-items-center mt-2">
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button type="submit" variant="success" size="sm">Salvar</b-button>
                </b-col>
                <b-col sm xs="12" class="text-center mt-2">
                  <b-button type="button" variant="danger" size="sm">Cancelar</b-button>
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
export default {
  name: "Despesa",
  data() {
    return {
      myModal: false,
      largeModal: false,
      smallModal: false,
      primaryModal: false,
      successModal: false,
      warningModal: false,
      dangerModal: false,
      infoModal: false
    };
  }
};
</script>

<style>
#valor {
  text-align: center;
}
</style>
