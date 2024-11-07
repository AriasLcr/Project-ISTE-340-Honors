<script>
import getData from "../utils/getData";
import { ref } from "vue";

export default {
  setup() {
    const data = ref({ results: [] });

    async function fetchData(): Promise<void> {
      data.value = await getData("people/");
    }

    fetchData();

    return {
      data,
    };
  },
};
</script>

<template>
    <div>
        <h1>People</h1>
        <ul>
        <li v-for="person in data.results" :key="person.name">
            {{ person.name }}
        </li>
        </ul>
    </div>
</template>

<style lang="css" scoped>
h1 {
    color: #333;
}
</style>