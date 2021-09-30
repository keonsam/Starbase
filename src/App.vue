<template>
  <div id="app">
    <h1 class="heading">Generate Your team</h1>
    <ul class="list">
      <Character
        v-for="(character, index) in characters"
        :key="character"
        :id="character"
        @change="onChange(index)"
      />
    </ul>
  </div>
</template>

<script>
import Character from "./components/Character.vue";

export default {
  name: "App",
  components: {
    Character,
  },
  data() {
    return {
      characters: [],
    };
  },
  created() {
    while (this.characters.length < 3) {
      const randomCharacter = Math.floor(Math.random() * 83) + 1;
      if (this.characters.indexOf(randomCharacter) === -1)
        this.characters.push(randomCharacter);
    }
  },
  methods: {
    onChange(index) {
      let loop = true;
      while (loop) {
        const randomCharacter = Math.floor(Math.random() * 83) + 1;
        if (this.characters.indexOf(randomCharacter) === -1) {
          this.characters.splice(index, 1, randomCharacter);
          loop = false;
        }
      }
    },
  },
};
</script>

<style>
body {
  background: #263238;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  color: white;
}

.heading {
  margin-bottom: 50px;
}

.list {
  list-style: none;
  margin: 0;
  padding: 0 10px;
  display: flex;
  gap: 10px;
}
</style>
