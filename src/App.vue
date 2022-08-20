<template>
  <h1>Currency Converter</h1>
  <div class="line">
    <Conversor currency-a="USD" currency-b="BRL" />
    <Conversor currency-a="BRL" currency-b="USD" />
  </div>
  <div class="line">
    <Conversor currency-a="CAD" currency-b="BRL" />
    <Conversor currency-a="BRL" currency-b="CAD" />
  </div>
  <div class="line">
    <Conversor currency-a="EUR" currency-b="BRL" />
    <Conversor currency-a="BRL" currency-b="EUR" />
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";
export default {
  name: "App",
  components: {
    Conversor,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.line {
  display: flex;
  justify-content: center;
  gap: 20px;
}
</style>
