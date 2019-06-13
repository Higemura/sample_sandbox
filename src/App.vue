<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png">
    <section>
      <button id="jquery" v-on:click="clickJquery()">jQuery あああああ</button>
      <div id="jquery-changed">jQuery いいいいい</div>
      <button id="vue" v-on:click="clickVue()">{{ msg1 }}</button>
      <div id="vue-changed">{{ msg2 }}</div>
    </section>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  data() {
    return {
      msg1: "Vue あああああ",
      msg2: "Vue うううううう"
    };
  },
  components: {
    HelloWorld
  },
  methods: {
    clickJquery() {
      const $jquery = $("#jquery");
      const $jqueryChanged = $("#jquery-changed");
      const value = $jquery.text();

      console.log(value);

      // jQuery: IDで取得した値をID箇所に格納
      $jqueryChanged.text(value);

      // Vue: DOMで取得した値をでデータに格納
      this.msg2 = value;
    },
    clickVue() {
      const $jquery = $("#jquery");
      const $jqueryChanged = $("#jquery-changed");

      console.log(this.msg1);

      // jQuery: データバインドした値をIDで取得したDOMに格納
      $jqueryChanged.text(this.msg1);

      // Vue: データバインドした値を別のデータに格納
      this.msg2 = this.msg1;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  cursor: pointer;
  &:hover {
    background-color: #ddd;
  }
}
</style>
