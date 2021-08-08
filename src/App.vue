<template>
  <div id="app">
    <Titulo msg="Random Gif Cat" />
    <Form />
  </div>
</template>

<script>
import Form from "@/components/Form.vue";
import Titulo from "@/components/Titulo.vue";
export default {
  name: "App",
  components: {
    Form,
    Titulo,
  },
};
</script>

<style>
body {
  background-color: aqua;
}
</style>
