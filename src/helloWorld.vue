<template>
  <h1>Hello World VUE Js 3</h1>
  <p>I'm {{ name }}, from {{ country }}.</p>
  <p v-html="rawHTML"></p>
</template>

<script>
export default {
  data() {
    return {
      rawHTML: "<b> HTML </b>",
      name: "Arsalan Ahmed Siddique",
      country: "Pakistan",
    };
  },

  //   beforeCreate() {
  //     console.log("beforeCreate was called.");
  //   },
  //   created() {
  //     console.log("created was called.");
  //   },
  //   beforeMount() {
  //     console.log(this.name);
  //     console.log("beforeMount was called.");
  //   },
  //   mounted() {
  //     console.log("mounted was called.");
  //     // debugger;
  //   },
  //   beforeUnmount() {
  //     console.log("beforeUnmounted was called.");
  //   },
  //   unmounted() {
  //     console.log("unmounted was called.");
  //   },

  methods: {
    showAlert() {
      alert("Alert Called by method.");
    },
  },
  mounted() {
    this.showAlert();
  },
};
</script>

<style scoped>
</style>