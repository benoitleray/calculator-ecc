<template>
    <div class="">
      <label for="benchmark" class="">Select Benchmark</label>
      <select v-model="selected" @change="updateBenchmark" class="">
        <option v-for="benchmark in benchmarks" :key="benchmark.description" :value="benchmark">
          {{ benchmark.description }}
        </option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selected: null,
        benchmarks: [
          { description: 'Promotional email', openRate: 50, clickRate: 3, conversionRate: 7 },
          { description: 'Request Sales email', openRate: 50, clickRate: 3, conversionRate: 1 },
          { description: 'Awareness email', openRate: 55, clickRate: 5, conversionRate: 11 },
          { description: 'Educational email', openRate: 50, clickRate: 4, conversionRate: 11 },
        ],
      };
    },
    methods: {
      updateBenchmark() {
        this.$emit('benchmark-selected', this.selected);
      },
    },
  };
  </script>
  