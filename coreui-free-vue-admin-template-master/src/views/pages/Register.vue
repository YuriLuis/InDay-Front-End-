<template>
  <div class="app flex-row align-items-center">
    <div class="container">
      <b-row class="justify-content-center">
        <b-col md="6" sm="8">
          <b-card no-body class="mx-4">
            <b-card-body class="p-4">
              <b-form>
                <h1>Login</h1>
                <p class="text-muted">Entrar ou Criar conta</p>
                <b-input-group class="mb-3">
                  <b-input-group-prepend>
                    <b-input-group-text>
                      <i class="icon-user"></i>
                    </b-input-group-text>
                  </b-input-group-prepend>
                  <b-form-input
                    type="text"
                    class="form-control"
                    placeholder="Nome de usuário"
                    autocomplete="Nome de usuário"
                    v-model="obj.usuario"
                  />
                </b-input-group>

                <b-input-group class="mb-3">
                  <b-input-group-prepend>
                    <b-input-group-text>@</b-input-group-text>
                  </b-input-group-prepend>
                  <b-form-input
                    type="text"
                    class="form-control"
                    placeholder="Email"
                    autocomplete="email"
                    v-model="obj.email"
                  />
                </b-input-group>

                <b-input-group class="mb-3">
                  <b-input-group-prepend>
                    <b-input-group-text>
                      <i class="icon-lock"></i>
                    </b-input-group-text>
                  </b-input-group-prepend>
                  <b-form-input
                    type="password"
                    class="form-control"
                    placeholder="Senha"
                    autocomplete="Nova senha"
                    v-model="obj.senha"
                  />
                </b-input-group>

                <b-input-group class="mb-4">
                  <b-input-group-prepend>
                    <b-input-group-text>
                      <i class="icon-lock"></i>
                    </b-input-group-text>
                  </b-input-group-prepend>
                  <b-form-input
                    type="password"
                    class="form-control"
                    placeholder="Repetir senha"
                    autocomplete="Repetir senha"
                    v-model="confSenha"
                  />
                </b-input-group>

                <b-button variant="success" block @click="CriarConta(obj)">Criar conta</b-button>
              </b-form>
            </b-card-body>
            <b-card-footer class="p-4">
              <b-row>
                <b-col cols="6"></b-col>
                <b-col cols="6"></b-col>
              </b-row>
            </b-card-footer>
          </b-card>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Register",
  data() {
    return {
      obj: {
        usuario: "",
        email: "",
        senha: ""
      },
      registroBancos: [],
      confSenha: "",
      taLogado: false
    };
  },
  methods: {
    CriarConta(obj) {
    
      if (!this.VerificaUsuarioExistente(obj)) {
          this.SalvarRegistroUsuario(obj)
          this.$router.replace("/dashboard")
      }else{
         this.$router.replace("/Pages/Register")
      }
    },
    CarregaListaUsuarios() {
      axios
      .get("http://localhost:8080/login")
      .then(response => {
        this.registroBancos.push(response.data);
      });
    },
    SalvarRegistroUsuario(obj) {
      axios
      .post("http://localhost:8080/login",this.obj)
      .then(response => {
        this.obj = response.data;
      });
    },
    VerificaUsuarioExistente(obj){
     axios
     .post("http://localhost:8080/login/autentica/",this.obj)
     .then(response => {
       console.log(response.data);
      })
      
      }
  }
};
</script>
