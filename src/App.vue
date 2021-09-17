<template>
  <div>
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Job finder</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/jobList.vue";
export default defineComponent({
  name: "App",
  components: {
    JobList
  },
  setup() {
    // const state = reactive({
    //   name: "Kanmi",
    //   age: 25 as number | string
    // });

    // return { ...toRefs(state) };

    // const name = ref("Kanmi");
    // const age = ref<number | string>(25);
    // return { name, age };

    const jobs = ref<Job[]>([
      {
        title: "Software Engineer",
        location: "London",
        salary: 50000,
        id: "1"
      },
      {
        title: "UI designer",
        location: "Germany",
        salary: 45000,
        id: "2"
      },
      {
        title: "QA tester",
        location: "Canada",
        salary: 52000,
        id: "3"
      },
      {
        title: "Product manager",
        location: "Australia",
        salary: 85000,
        id: "4"
      }
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
  // data() {
  //   return {
  //     name: "Kanmi",
  //     age: 25 as number | string
  //   };
  // },
  methods: {
    // changeName(newName: string) {
    //   this.name = newName;
    // },
    // changeAge(age: number | string) {
    //   this.age = age;
    // }
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
header .title {
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
