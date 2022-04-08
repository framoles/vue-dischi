<template>
  <main>
    <div v-for="(item, index) in array" :key="index">
      <img :src="item.poster" :alt="item.title" />
      <p>{{ item.title }}</p>
      <p>{{ item.author }}</p>
      <p>{{ item.year }}</p>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "MainComp",

  data() {
    return {
      array: Array,
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.array = resp.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
main {
  display: flex;
  column-gap: 30px;
  div {
    width: 100px;
    background-color: rgb(37, 35, 56);
    padding: 10px;
    color: white;
    img {
      width: 100%;
    }
  }
}
</style>