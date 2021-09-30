<template>
  <li class="card" @click="$emit('change')">
    <h2 class="card-title">{{ character.name }}</h2>
    <p class="card-text">Height: {{ character.height }}</p>
    <p class="card-text">Mass: {{ character.mass }}</p>
    <p class="card-text">Hair Color: {{ character.hair_color }}</p>
    <p class="card-text">Eye Color: {{ character.eye_color }}</p>
  </li>
</template>

<script>
export default {
  name: "Character",
  props: {
    id: Number,
  },
  data() {
    return {
      character: {},
    };
  },
  created() {
    this.getCharacter(this.id);
  },
  methods: {
    getCharacter(id) {
      fetch(`https://swapi.dev/api/people/${id}/`, {
        method: "GET",
      })
        .then((res) => res.json())
        .then((data) => {
          if (data) this.character = data;
        });
    },
  },
};
</script>

<style scoped>
.card {
  border: 2px solid #4fc08d;
  border-radius: 4px;
  cursor: pointer;
  padding: 15px;
  flex: 1;
}
</style>
