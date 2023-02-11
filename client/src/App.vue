<template>
    <div class="container">
      <div class="row">
        <header>
          Dashboard Olympia
        </header>
      </div>
    <div class="row">
      <DropdownComp @countryChange="onCountryChange($event)" :options="countryOptions"></DropdownComp>
      <DropdownComp @eventChange="onEventChange($event)" :options="eventOptions"></DropdownComp>
    </div>
    <div class="row">
      <header>
      Medals:
      </header>
      <div class="col">
        <TableComp :options="{'country': country, 'event': event}"></TableComp>
        <PlotlyComp :options="{'country': country, 'event': event}"></PlotlyComp>
      </div>
      <div class="col">
      </div>

    </div>
  </div>

</template>

<style scoped>
@import "bootstrap";
header {
  font-size: x-large;
}
</style>

<script setup>
import PlotlyComp from "./components/PlotlyComp.vue";
import TableComp from "./components/TableComp.vue";
import DropdownComp from "./components/DropdownComp.vue"
</script>

<script>
export default {

  data() {
    return {
        country: "", 
        event: "",
        countryOptions: "country",
        eventOptions: "event"
    };
  },   
  methods: {
    onCountryChange(value) {
      this.country = value;
    }, 
    onEventChange(value) {
      this.event = value; 
    }
  }
}
</script>