<template>
  <div>
    <h1>Detalles del espacio</h1>
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
          to: { name: "Catalago" },
        },
        {
          text: "Detalles",
          to: { name: "Detalles" },
          active: true
        },
      ],
    };
  },
}
</script>

<style></style>