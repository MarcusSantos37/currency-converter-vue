<template>
  <div class="conversor">
    <h2>{{ currencyA }} to {{ currencyB }}</h2>
    <input
      type="text"
      v-model="currencyA_value"
      v-bind:placeholder="currencyA"
    />
    <input type="button" value="Convert" v-on:click="convert" />
    <h2>{{ currencyB_value }}</h2>
  </div>
</template>

<script>
export default {
  name: "Conversor",
  props: ["currencyA", "currencyB"],
  data() {
    return {
      currencyA_value: "",
      currencyB_value: 0,
    };
  },
  methods: {
    convert() {
      var myHeaders = new Headers();
      myHeaders.append("apikey", "HKYZ6mY5EAQ82JkOsMP6utQRTrKihS6t");

      var requestOptions = {
        method: "GET",
        redirect: "follow",
        headers: myHeaders,
      };

      let from = this.currencyA;
      let to = this.currencyB;
      let value = this.currencyA_value;

      let url =
        "https://api.apilayer.com/exchangerates_data/convert?to=" +
        to +
        "&from=" +
        from +
        "&amount=" +
        value;

      fetch(url, requestOptions)
        .then((res) => {
          return res.json();
        })
        .then((json) => {
          this.currencyB_value = json.result.toFixed(2);
        });
    },
  },
};
</script>

<style scope>
.conversor {
  padding: 20px;
  max-width: 300px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;

  border-radius: 5px;
}
</style>
