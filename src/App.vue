<template>
  <div>
    <div v-for="item in valor">
      {{ item.title }}
      <SoyUnComponente :api="item" />
      <hr />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SoyUnComponente from "@/components/SoyUnComponente.vue";

export default {
  components: {
    SoyUnComponente,
  },

  data() {
    return {
      valor: [],
    };
  },
  methods: {
    consumirApi: function (api) {
      axios
        .get(api)
        .then((res) => {
          this.valor = res.data;
          console.log(this.valor)
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
  created: function () {
    this.consumirApi("https://stoplight.io/mocks/modyo/pcfactory-documentation/79796109/campanas/ofertas-videojuegos");
  },
  mounted: function () {},
};
</script>

<style scoped></style>
