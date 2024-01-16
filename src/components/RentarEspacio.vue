<template>
  <div >
    <h1 class="mr-4">Renta tu espacio</h1>
    <b-breadcrumb :items="items"></b-breadcrumb>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          text: "Renta tu espacio",
          to: { name: "Rentar" },
          active: true
        },
        {
          text: "Información",
          to: { name: "Informacion" },
        },
        {
          text: "Ofertar",
          to: { name: "Ofertar" },
        },
      ],
    };
  },
}
</script>

<style>
</style>