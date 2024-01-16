<template>
  <div>
    <h1>Información del espacio</h1>
    <b-breadcrumb :items="items"></b-breadcrumb>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          text: "Rentar tu espacio",
          to: { name: "Rentar" },
         
        },
        {
          text: "Información",
          to: { name: "Informacion" },
          active: true
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

<style></style>