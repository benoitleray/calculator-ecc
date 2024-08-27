<template>
    <div class="">
      <h2 class="">Results</h2>
      <div class="">
        <!-- Option 1: Amount of Emails -->
        <div>
          <h3 class="">Option 1: Customer Reach Target:</h3>
          <input type="number" v-model="revenueTarget" placeholder="Revenue Target ($)" @input="calculateEmails" class="p-2 border rounded" />
        
          <input type="number" v-model="conversionValue" placeholder="Conversion Value ($)" @input="calculateEmails" class="mt-2 p-2 border rounded" />
          <div class="">Customer Reach Target: <strong>{{ amountOfEmails }}</strong></div>
        </div>
  
        <!-- Option 2: Estimated Revenue -->
        <div>
          <h3 class="">Option 2: Estimated Revenue</h3>
          <input type="number" v-model="availableContacts" placeholder="Available Contacts" @input="calculateRevenue" class="p-2 border rounded" />
          <input type="number" v-model="conversionValue" placeholder="Conversion Value ($)" @input="calculateRevenue" class="mt-2 p-2 border rounded" />
          <div class="">Estimated Revenue: <strong>{{ estimatedRevenue }}</strong></div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['ecc'],
    data() {
      return {
        revenueTarget: 0,
        conversionValue: 0,
        availableContacts: 0,
        amountOfEmails: 0,
        estimatedRevenue: 0,
      };
    },
    methods: {
      calculateEmails() {
        if (this.ecc && this.revenueTarget && this.conversionValue) {
          this.amountOfEmails = Math.round((this.ecc * this.revenueTarget) / this.conversionValue);
        }
      },
      calculateRevenue() {
        if (this.ecc && this.availableContacts && this.conversionValue) {
          this.estimatedRevenue = Math.round((this.availableContacts * this.conversionValue) / this.ecc);
        }
      },
    },
  };
  </script>
  