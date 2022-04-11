<template>
  <main>
    <header>
      <select @change="displaySelected($event)">
        <option value="Genere">Genere</option>
        <option value="Pop">Pop</option>
        <option value="Metal">Metal</option>
        <option value="Jazz">Jazz</option>
        <option value="Rock">Rock</option>
      </select>
    </header>
    <footer>
      <div v-for="(item, index) in filtered" :key="index">
        <img :src="item.poster" :alt="item.title" />
        <p>{{ item.title }}</p>
        <p>{{ item.author }}</p>
        <p>{{ item.year }}</p>
      </div>
    </footer>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "MainComp",

  data() {
    return {
      array: Array,
      genere: "Genere",
      filtered: Array,
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.array = resp.data.response;
        this.filtered = this.array;
      });
  },
  methods: {
    displaySelected(event) {
      this.genere = event.target.value;

      if (this.genere == "Genere") {
        this.filtered = this.array;
      } else {
        const result = this.array.filter((item) => {
          return item.genre.includes(this.genere);
        });

        this.filtered = result;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  select {
    margin-bottom: 20px;
    font-size: 20px;
    border: 2px dotted red;
  }
}
footer {
  display: flex;
  column-gap: 30px;
  background-color: rgb(53, 67, 145);
  div {
    width: calc((100% / 5) - 30px);
    background-color: rgb(86, 110, 243);
    padding: 10px;
    color: white;
    img {
      width: 100%;
    }
  }
}
</style>