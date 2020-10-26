<template>
<v-app>
    <div>
        <H1>This is the current Bitcoin price!</H1>
        <p>{{ info }}</p>
    </div>
</v-app>
</template>

<script>
import axios from 'axios';
export default {
  name: "AppBitcoinPayloadCall",
  props: {
    msg: String
  },
  data: function(){
      return {
          info:null
      }
  },
  mounted: function(){
      axios.get('http://localhost:8081/cms-storage/all-job-listings').then(response => console.log(response.data));
      axios.get('https://api.coindesk.com/v1/bpi/currentprice.json').then(response => console.log(response.data));
      axios.get('https://api.coindesk.com/v1/bpi/currentprice.json').then(response => this.info = response.data.bpi);
  }

};
</script>