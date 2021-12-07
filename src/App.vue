<template>
  <v-app>
    <v-app-bar app color="green darken-3" dark>
      <v-container>
        <h1>Mock API</h1>
      </v-container>
    </v-app-bar>

    <v-main class="mt-12 pt-12">
      <v-container>
        <v-row>
          <v-col
            lg="3"
            md="3"
            v-for="producto in productos"
            :key="producto.ConvertInvalidComponents"
          >
            <v-card class="pa-2">
              <img style="max-width: 100%" :src="producto.image" alt="">
              <h3>{{ producto.nombre }}</h3>
              <p class="mb-0">Precio: {{ producto.precio }}</p>
              <p>Cantidad: {{ producto.cantidad }}</p>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      productos: [],
    };
  },
  mounted() {
    fetch("https://61afe8fa3e2aba0017c49598.mockapi.io/productos")
      .then((res) => res.json())
      .then((data) => {
        this.productos = data;
        console.log(data);
      });
  },
};
</script>

<style lang="scss" scoped></style>
