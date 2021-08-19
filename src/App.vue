<template>
  <div id="app">
    <form @submit.prevent="saveData">
      <label for="bb">Auto</label>
      <input type="text" placeholder="Wpisz serwisowae auto" v-model="auto" />
      <button>WYSLIJ</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      auto: "",
    };
  },
  methods: {
    saveData() {
      console.log(this.auto);
    },
  },
};
</script>

<style></style>
