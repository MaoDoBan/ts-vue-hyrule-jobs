<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="Site Logo">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="ordenar('title')">ordenar por título</button>
        <button @click="ordenar('salary')">ordenar por salário</button>
        <button @click="ordenar('location')">ordenar por local</button>
      </div>
    </header>

    <JobList :jobs="jobs" :ordem="ordem"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/Job";
import PropVaga from "./types/PropVaga";

export default defineComponent({
  name: "App",
  components: {JobList},
  setup(){
    const jobs = ref<Job[]>([
      {title: "farm worker",  location: "lon lon ranch",  salary: 30000, id: "1"},
      {title: "quarryman",    location: "death mountain", salary: 40000, id: "2"},
      {title: "flute player", location: "the lost woods", salary: 35000, id: "3"},
      {title: "fisherman",    location: "lake hylia",     salary: 21000, id: "4"},
      {title: "prison guard", location: "gerudo valley",  salary: 32000, id: "5"}
    ]);

    const ordem = ref<PropVaga>("title");
    function ordenar(tipo: PropVaga){
      ordem.value = tipo;
    }

    return {jobs, ordenar, ordem};
  }
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
