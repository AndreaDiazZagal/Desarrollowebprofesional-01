<script setup>
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
</script>

<template>
  <div id="app">
    <b-navbar toggleable="lg" z-index="15" type="dark" variant="info">
      <b-navbar-brand href="#" style="margin-left: 20px"
        >EspacioVivo
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">Link</b-nav-item>
          <b-nav-item href="#" disabled>Disabled</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <b-container fluid>
      <b-row>
        <b-col>
          <b-sidebar
            id="sidebar-1"
            sidebar-class="border"
            backdrop-variant="transparent"
            backdrop
            no-close-on-backdrop
            no-close-on-esc
            no-close-on-route-change
            no-header-close
            title="Sidebar"
            visible
            z-index="-1"
          >
            <b-nav > 
              <b-nav-item > 
                <b-link :to="{ name: 'Rentar' }" class="b-nav-link">
                  <b-icon icon="house-door" class="mr-2"></b-icon> Renta tu
                  espacio
                </b-link>
              </b-nav-item>
              <b-nav-item>
                <b-link :to="{ name: 'RentarTEspacio' }" class="b-nav-link">
                  <b-icon icon="building" class="mr-2"></b-icon> Rentar espacio
                </b-link>
              </b-nav-item>
            </b-nav>
          </b-sidebar>
        </b-col>
        <b-col>
          <router-view></router-view>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script></script>

<style scoped>
/* Estilos personalizados para desactivar el subrayado azul y cambiar el color de fondo */
.b-nav-link {
  text-decoration: none !important; /* Desactivar el subrayado azul */
  background-color: transparent !important; /* Fondo transparente por defecto */
  color: black !important; /* Cambiar el color del texto a negro */
}
</style>
