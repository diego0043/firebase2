<template>
  <div>
    <v-container>
      <v-row>
        <v-col cols="6">
          <fotos></fotos>
        </v-col>

       
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Fotos from "./components/Fotos.vue";

export default {
  name: "App",

  components: {
    Fotos,
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>

</style>
