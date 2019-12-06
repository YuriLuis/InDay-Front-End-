<template>
  <div>
    <div class="col">
        <div class="wrapper">
          <div class="animated fadeIn">
            <b-card-header>
              <strong>Categoria</strong>
            </b-card-header>
            <table class="table table-hover">
              <thead class="bg-success">
                <tr>
                  <th scope="col">Descrição</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="categoria in categorias" :key="categoria.descricao">
                  <td >{{categoria.descricao}}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>  
  </div>
</template>

<script>

import axios from "axios";
export default {
  data() {
    return {
      categorias: []
    };
  },
  methods: {
    GetCategorias() {
      axios.get("http://localhost:8080/categoria").then(response => {
        this.categorias = response.data;
      });
    }
  },
  watch:{
      categorias: function(val){
       this.GetCategorias()
      }
    },
    mounted(){
        this.GetCategorias();
    }
};
</script>

<style>
</style>