<template>
  <div>
    <h1>Rentar espacio</h1>
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
          active: true
        },
        {
          text: "Catalogo ",
          to: { name: "Catalago" },
        },
        {
          text: "Detalles ",
          to: { name: "Detalles" },
        },
      ],
    };
  },
}
</script>

<style></style>
