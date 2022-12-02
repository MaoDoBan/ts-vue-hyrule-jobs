<template>
  <div class="job-list">
    <p>Ordenação: {{ordem}}</p>
    <ul>
      <li v-for="job in vagasOrdenadas" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Rem omnis voluptatum eius doloremque optio iusto sequi dignissimos.</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Job from "@/types/Job"; //@ é o root do projeto
import PropVaga from "@/types/PropVaga";
import { computed, defineComponent, PropType } from "vue";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    ordem: {
      required: true,
      type: String as PropType<PropVaga>
    }
  },
  setup(props){
    const vagasOrdenadas = computed(() => [...props.jobs].sort(
      (job1: Job, job2: Job) => job1[props.ordem] > job2[props.ordem] ? 1 : -1
    ));

    return {vagasOrdenadas};
  }
})
</script>

<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0;
  }
  .job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }
</style>