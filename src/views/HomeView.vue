<script>
import axios from "axios";

export default {
  name: "jobs",
  data() {
    return {
      jobs: [],
    };
  },
  mounted() {
    this.getJobs();
  },
  methods: {
    getJobs() {
      axios.get("http://localhost:9091/api/v1/jobs/").then((res) => {
        this.jobs = res.data;
        console.log(this.jobs);
      });
    },
  },
};
</script>

<template>
  <main>
    <h1 class="text-center">Jobs</h1>
    <div class="container">
      <button class="btn btn-primary">+ New Job</button>
      <table class="table">
        <thead class="table-dark">
          <tr>
            <th>id</th>
            <th>Name</th>
            <th>JobClass</th>
            <th>CRON</th>
            <th>Active</th>
            <th>Created</th>
            <th>Latest</th>
            <th>Websites</th>
            <th>Cities</th>
            <th>####</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in this.jobs" :key="index">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.jobClass }}</td>
            <td>{{ item.cron }}</td>
            <td>{{ item.active }}</td>
            <td>{{ item.createdOn }}</td>
            <td>{{ item.lastExecutedOn }}</td>
            <td>{{ item.websites }}</td>
            <td>{{ item.cities }}</td>
            <td>
              <button class="btn btn-warning">Edit</button>
              <button class="btn btn-danger">Del</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </main>
</template>
