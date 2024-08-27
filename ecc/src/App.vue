<template>

    <div>
     <div>        <HeaderComponent />
        <BenchmarkSelector @benchmark-selected="handleBenchmarkSelected" />
        <ECCCalculator :benchmark="selectedBenchmark" @ecc-calculated="handleECCCalculated" />
        <ResultOptions :ecc="eccValue" />
        <FooterComponent />
      </div>

    </div>

</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import HeaderComponent from './components/HeaderComponent.vue';
import BenchmarkSelector from './components/BenchmarkSelector.vue';
import ECCCalculator from './components/ECCCalculator.vue';
import ResultOptions from './components/ResultOptions.vue';
import FooterComponent from './components/FooterComponent.vue';

export default {
  components: {
    HeaderComponent,
    BenchmarkSelector,
    ECCCalculator,
    ResultOptions,
    FooterComponent,
  },
  data() {
    return {
      selectedBenchmark: null,
      eccValue: 0,
    };
  },
  methods: {
    handleBenchmarkSelected(benchmark) {
      this.selectedBenchmark = benchmark;
    },
    handleECCCalculated(ecc) {
      this.eccValue = ecc;
    },
  },
};
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>