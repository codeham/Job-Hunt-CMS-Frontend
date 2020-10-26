<template>
<v-app>
  {{ name }}
  <v-data-table :headers="headers" :items="jobPosts" class="elevation-1">
    <template v-slot:[`item.jobStatus`]="{ item }">
      <v-chip :color="getColor(item.jobStatus)" dark>
        {{ item.jobStatus }}
      </v-chip>
    </template>
  </v-data-table>
</v-app>
</template>

<script>
import axios from 'axios';
export default {
  name: "DataTableJobListings",
  async created() {    
    const jobListingsData = await this.getJobListings();
    this.jobPosts = jobListingsData;
  },
  props: { 
    "name" : {
      type: String,
      default: ""
    }
  },
  data: function() {
    return {
      inputState: "",
      jobPosts: [],
      headers: [
        {
          text: "Company",
          align: "start",
          sortable: "true",
          value: "company",
        },
        { text: "Position", value: "position" },
        { text: "Platform", value: "platform" },
        { text: "City", value: "city" },
        { text: "State", value: "state" },
        { text: "Country", value: "country" },
        { text: "Description", value: "description" },
        { text: "Requirements", value: "requirements" },
        { text: "Date Applied", value: "postingDate" },
        { text: "Job Status", value: "jobStatus" },
      ],

    };
  },
    methods: {
        getColor(status) {
          if (status === "Applied") {
            return "green";
          } else if (status === "Denied") {
            return "red";
          } else {
            return "orange";
          }
        },
        async getJobListings() {
          const { data: responseData } = await axios.get('http://localhost:8081/cms-storage/all-job-listings')
          return responseData;
        }
      },
};
</script>
