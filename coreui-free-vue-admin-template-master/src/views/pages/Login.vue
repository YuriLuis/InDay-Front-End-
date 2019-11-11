<template>
  <div class="app flex-row align-items-center">
    <div class="container">
      <b-row class="justify-content-center">
        <b-col md="5">
          
            <b-card no-body class="p-4">
              
                <b-form>
                  <b-row>
                <b-col cols="6">
                  <b-button block class="btn btn-facebook"><span>facebook</span></b-button></p>
                </b-col>
                <b-col cols="6">
                  <b-button block class="btn btn-gmail" type="button"><span>gmail</span></b-button></p>
                </b-col>
              </b-row>
        
                  <b-input-group class="mb-3">
                    <b-input-group-prepend><b-input-group-text><i class="icon-user"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input type="text" class="form-control" placeholder="" autocomplete="username email" />
                  </b-input-group>
                  <b-input-group class="mb-4">
                    <b-input-group-prepend><b-input-group-text><i class="icon-lock"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input type="password" class="form-control" placeholder="" autocomplete="current-password" />
                  </b-input-group>
                  <b-row>
                    <b-col cols="2" class="text-center">
                      <b-button variant="primary" >Entrar</b-button>
                    </b-col>
                    <b-col cols="10" class="text-right">
                      <b-button variant="link" class="px-0">Esqueci minha senha</b-button>
                    </b-col>
                  </b-row>
                </b-form>
              </b-card-body>
            </b-card>
            
              <b-card-body class="text-center">
          
              </b-card-body>
            </b-card>
          </b-card-group>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login'
}
</script>
