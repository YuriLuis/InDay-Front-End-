<template>
    <AppHeader fixed>
      <!--<SidebarToggler class="d-lg-none" display="md" mobile />-->
      <b-link class="navbar-brand" to="#">
        <img class="navbar-brand-full" src="img/brand/inday.png" width="89" height="25" alt="CoreUI Logo">
        <img class="navbar-brand-minimized" src="img/brand/sygnet.svg" width="30" height="30" alt="CoreUI Logo">
      </b-link>
      <!--<SidebarToggler class="d-md-down-none" display="lg" :defaultOpen=true />-->
      <b-navbar-nav class="d-md-down-none">
        <b-nav-item class="px-3" to="/dashboard" >Início</b-nav-item>
        <b-nav-item class="px-3" to="/modal" exact>Lançamentos</b-nav-item>
        <b-nav-item class="px-3">Relatórios</b-nav-item>
        <b-nav-item class="px-3" to="/metas" exact>Metas</b-nav-item>
        <b-nav-item class="px-3" to="/categoria" exact>Categoria</b-nav-item>
      </b-navbar-nav>
      <b-navbar-nav class="ml-auto">
        <!--
        <b-nav-item class="d-md-down-none">
          <i class="icon-bell"></i>
          <b-badge pill variant="danger">5</b-badge>
        </b-nav-item>
        <b-nav-item class="d-md-down-none">
          <i class="icon-list"></i>
        </b-nav-item>
        <b-nav-item class="d-md-down-none">
          <i class="icon-location-pin"></i>
        </b-nav-item>
        <DefaultHeaderDropdownAccnt/> -->
      </b-navbar-nav> 
      <!--<AsideToggler class="d-none d-lg-block" />
      <AsideToggler class="d-lg-none" mobile />-->
    </AppHeader>
</template>
<script>
import { Header as AppHeader, SidebarToggler, AsideToggler } from '@coreui/vue'
import DefaultHeaderDropdownAccnt from './DefaultHeaderDropdownAccnt'

export default {
  name: 'DefaultHeader',
  components: {
    AsideToggler,
    AppHeader,
    DefaultHeaderDropdownAccnt,
    SidebarToggler
  }
}
</script>
