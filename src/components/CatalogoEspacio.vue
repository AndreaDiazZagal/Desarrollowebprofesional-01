<template>
  <div>
    <h1>Catalogo de espacios</h1>
    <b-breadcrumb :items="items"></b-breadcrumb>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          text: "Rentar espacio",
          to: { name: "RentarTEspacio" },
        },
        {
          text: "Catalogo",
          to: { name: "Catalogo" },
          active: true
        },
        {
          text: "Detalles",
          to: { name: "Detalles" },
        },
      ],
    };
  },
}
</script>

<style></style>