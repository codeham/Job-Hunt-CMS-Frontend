<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
  <v-row>
    <v-col>
      <v-text-field
      v-model="company"
      :counter="10"
      :rules="companyRules"
      label="Company"
      required
      ></v-text-field>
    </v-col>
    <v-col>
      <v-text-field
        v-model="position"
        :rules="positionRules"
        label="Position"
        required
      ></v-text-field>    
    </v-col>
  </v-row>

  <v-row>
    <v-col>
      <v-text-field
        v-model="city"
        :rules="cityRules"
        label="City"
        required
      ></v-text-field>
    </v-col>
    <v-col>
      <v-select
        v-model="selectState"
        :items="states"
        :rules="[v => !!v || 'State is required']"
        label="State"
        required
      ></v-select>
    </v-col>
  </v-row>

  <v-row>
    <v-col>
      <v-select
        v-model="selectCountry"
        :items="country"
        :rules="[v => !!v || 'Country is required']"
        label="Country"
        required
      ></v-select>
    </v-col>
    <v-col>
      <v-select
        v-model="selectJobPlatform"
        :items="jobPlatform"
        :rules="[v => !!v || 'Country is required']"
        label="Job Plaform"
        required
      ></v-select>   
    </v-col>
  </v-row>

  <v-row>
      <v-col
        cols="12"
        md="6"
      >
        <v-textarea
          v-model="requirements"
          name="input-7-1"
          label="Job Requirements"
          value=""
          hint="Job Requirements"
        ></v-textarea>
      </v-col>
      <v-col
        cols="12"
        md="6"
      >
        <v-textarea
          v-model="description"
          name="input-7-1"
          label="Description"
          value=""
          hint="Job Description"
        ></v-textarea>
      </v-col>
  </v-row>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>

    <v-btn
      color="success"
      @click="submitForm"
    >
      Submit
    </v-btn>
  </v-form>
</template>

<script>
import axios from 'axios';
  export default {
    data: () => ({
      valid: true,
      company: '',
      companyRules: [
        v => !!v || 'Company is required',
        v => (v && v.length <= 10) || 'Company name must be less than 10 characters',
      ],
      position: '',
      positionRules: [
        v => !!v || 'Position is required'
      ],
      city:'',
      cityRules: [],
      state:'',
      stateRules: [],
      selectState: null,
      states: [
        'Alabama', 'Alaska', 'American Samoa', 'Arizona', 'Arkansas', 'California', 'Colorado', 'Connecticut', 'Delaware', 'District of Columbia', 'Florida', 'Georgia', 'Guam', 'Hawaii', 'Idaho', 'Illinois', 'Indiana', 'Iowa', 'Kansas', 'Kentucky', 'Louisiana', 'Maine', 'Maryland', 'Massachusetts', 'Michigan', 'Minnesota', 'Minor Outlying Islands', 'Mississippi', 'Missouri', 'Montana', 'Nebraska', 'Nevada', 'New Hampshire', 'New Jersey', 'New Mexico', 'New York', 'North Carolina', 'North Dakota', 'Northern Mariana Islands', 'Ohio', 'Oklahoma', 'Oregon', 'Pennsylvania', 'Puerto Rico', 'Rhode Island', 'South Carolina', 'South Dakota', 'Tennessee', 'Texas', 'U.S. Virgin Islands', 'Utah', 'Vermont', 'Virginia', 'Washington', 'West Virginia', 'Wisconsin', 'Wyoming'
      ],
      selectCountry: null,
      country: ['United States'],
      selectJobPlatform: null,
      jobPlatform: ['Glassdoor', 'Indeed', 'LinkedIn', 'Monster','Other'],
      checkbox: false,
      description: null,
      requirements: null
    }),

    methods: {
      submitForm () {
        const requestObj = {company: this.company, position: this.position, city: this.city, state: this.selectState, platform: this.selectJobPlatform, country: this.selectCountry, description: this.description, requirements: this.requirements}
        console.log(this.company);
        axios.post('http://localhost:8081/cms-storage/testAPI', requestObj).then((response) => {console.log(response)});
      },
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }
</script>