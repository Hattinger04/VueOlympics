<template>
  <header>
    Dashboard Olympia
  </header>
  <CountryDropdownComp></CountryDropdownComp>
  <div class="container">
    <div class="row">
      <div class="col−sm">
        <TableComp></TableComp>
        <PlotlyComp></PlotlyComp>
      </div>
    </div>
  </div>

</template>

<style scoped>

header {
  font-size: x-large;
}
</style>

<script setup>
import PlotlyComp from "./components/PlotlyComp.vue";
import TableComp from "./components/TableComp.vue";
import CountryDropdownComp from "./components/CountryDropdownComp.vue"
</script>