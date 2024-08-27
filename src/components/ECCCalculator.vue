<template>
  <div>
    <h2 class="">ECC Calculation</h2>
    <div class="">

      <label for="openRate">Open Rate</label>
      <input name="openRate" type="number" v-model="openRate" placeholder="Open Rate (%)" @input="calculateECC"
        class="p-2 border rounded" />

      <label for="clickRate">Click Rate</label>
      <input name="clickRate" type="number" v-model="clickRate" placeholder="Click Through Rate (%)"
        @input="calculateECC" class="p-2 border rounded" />

      <label for="conversionRate">Conversion Rate</label>
      <input name="conversionRate" type="number" v-model="conversionRate" placeholder="Conversion Rate (%)"
        @input="calculateECC" class="p-2 border rounded" />
    </div>
    <div class="">
      <p class="">ECC: <strong>{{ ecc.toFixed(0) }}</strong></p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['benchmark'],
  data() {
    return {
      openRate: this.benchmark?.openRate || 0,
      clickRate: this.benchmark?.clickRate || 0,
      conversionRate: this.benchmark?.conversionRate || 0,
      ecc: 0,
    };
  },
  watch: {
    benchmark(newBenchmark) {
      this.openRate = newBenchmark.openRate;
      this.clickRate = newBenchmark.clickRate;
      this.conversionRate = newBenchmark.conversionRate;
      this.calculateECC();
    },
  },
  methods: {
    calculateECC() {
      const open = this.openRate / 100;
      const click = this.clickRate / 100;
      const conversion = this.conversionRate / 100;
      if (open && click && conversion) {
        this.ecc = 1 / (open * click * conversion);
        this.$emit('ecc-calculated', this.ecc);
      }
    },
  },
};
</script>