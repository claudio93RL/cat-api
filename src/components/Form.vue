
<template>
  <form @submit.prevent="consultaGato(datosGato)">
    <div class="rojo">
      <div class="mt-5 p-5">
        <div class="form-group row justify-content-center">
          <label class="col-sm-1 col-form-label col-form-label-lg"
            >Titulo:</label
          >
          <div class="col-sm-4">
            <input
              type="text"
              class="form-control form-control-lg"
              placeholder="texto"
              v-model="datosGato.titulo"
            />
          </div>
        </div>
        <div class="form-group row justify-content-center">
          <label class="col-sm-1 col-form-label col-form-label-lg"
            >Tamaño:</label
          >
          <div class="col-sm-4">
            <input
              type="number"
              class="form-control form-control-lg"
              placeholder="tamaño"
              v-model="datosGato.tamaño"
            />
          </div>
        </div>
        <div class="form-group row justify-content-center">
          <label class="col-sm-1 col-form-label col-form-label-lg"
            >Color:
          </label>
          <div class="col-sm-4">
            <select
              class="form-control custom-select"
              v-model="datosGato.color"
            >
              <option selected>red</option>
              <option>green</option>
              <option>blue</option>
            </select>
          </div>
        </div>
        <div class="form-group row justify-content-center">
          <label class="col-sm-1 col-form-label col-form-label-lg"
            >Filtro:</label
          >
          <div class="col-sm-4">
            <select
              class="form-control custom-select"
              v-model="datosGato.filtro"
            >
              <option selected>blur</option>
              <option>mono</option>
              <option>sepia</option>
              <option>negative</option>
              <option>pain</option>
              <option>pixel</option>
            </select>
          </div>
        </div>
      </div>
    </div>
    <div class="d-flex flex-column align-items-center">
      <button type="submit" class="btn btn-light mt-4 p-1">
        Obtener mi gatito
      </button>
      <img class="p-5" :src="fotoGato" alt="" />
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      datosGato: {
        titulo: "",
        tamaño: "",
        color: "",
        filtro: "",
      },
      fotoGato: "",
    };
  },
  methods: {
    async consultaGato(gato) {
      try {
        const { titulo, tamaño, color, filtro } = gato;
        const res = await fetch(
          `https://cataas.com/cat/gif/says/${titulo}?filter=${filtro}&color=${color}&size=${tamaño}&type=or`
        );
        this.fotoGato = res.url;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style>
.rojo {
  background-color: coral;
}
</style>