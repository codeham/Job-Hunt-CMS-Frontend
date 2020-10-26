<template>
  <v-app>
    <v-main>
       <v-container>
        <JobFormSubmissionComponent></JobFormSubmissionComponent>
      </v-container>
      <v-container class="">
        <!-- <DataTableComponent></DataTableComponent> -->
        <data-table-job-listing-component></data-table-job-listing-component>
        <!-- <AppBitcoinPayloadCall></AppBitcoinPayloadCall> -->
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
// import HelloWorld from "./components/HelloWorld";
// import DataBindingComponent from "./components/DataBindingComponent";
// import AppTestComponent from "./components/AppTestComponent";
// import DataTableComponent from "./components/DataTableComponent";
import DataTableJobListingComponent from "./components/DataTableJobListingsComponent";
import JobFormSubmissionComponent from "./components/JobFormSubmissionComponent";
// import AppBitcoinPayloadCall from "./components/AppBitcoinPayloadCall";

export default {
  name: "App",

  components: {
    // DataBindingComponent,
    // AppTestComponent,
    // DataTableComponent,
    DataTableJobListingComponent,
    JobFormSubmissionComponent
    // AppBitcoinPayloadCall
  },

  data: () => ({
    //
  })
};
</script>
