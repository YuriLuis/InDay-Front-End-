<template>
  <div class="app flex-row align-items-center">
    <div class="container">
      <b-row class="justify-content-center">
        <b-col md="5">
          
            <b-card no-body class="p-4">
                  <b-input-group class="mb-3">
                    <b-input-group-prepend><b-input-group-text><i class="icon-user"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input type="text" class="form-control" placeholder="" autocomplete="username email" />
                  </b-input-group>
                  <b-input-group class="mb-4">
                    <b-input-group-prepend><b-input-group-text><i class="icon-lock"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input type="password" class="form-control" placeholder="" autocomplete="current-password" />
                  </b-input-group>
                  <b-row>
                    <b-col cols="1" class="text-left">
                      <b-button variant="primary" @click="login()">Entrar</b-button>
                    </b-col>
                    <b-col cols="5" class="text-right">
                      <b-button variant="link" class="px-0" @click="Registrar()">Criar conta</b-button>
                    </b-col>
                    <b-col cols="6" class="text-right">
                      <b-button variant="link" class="px-0">Esqueci minha senha</b-button>
                    </b-col>
                  </b-row>
            </b-card>
            
              <b-card-body class="text-center">
              </b-card-body>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data(){
    return{}
  },
  methods:{
     login: function(){
      this.$router.replace("/dashboard");
    },
    Registrar : function(){
      this.$router.replace("/Pages/Register")
    }
   
  }
}
</script>
