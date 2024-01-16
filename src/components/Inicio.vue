<template>
  <div class="container text-center d-flex align-items-center ">
    <header>
      <h1>EspacioVivo</h1>
      <p>Encuentra el lugar perfecto para tu evento o vacaciones</p>
    </header>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          text: "Inicio",
          href: "#",
          to: { name: "Inicio" },
        },
        {
          text: "Main",
          href: "#",
          to: { name: "Main" },
        },
        {
          text: "Tercero",
          href: "#",
          to: { name: "Tercero" },
        },
      ],
    };
  },
};
</script>


