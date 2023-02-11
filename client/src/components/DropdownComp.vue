<template>
  <select v-model="item" @change="onChange($event)">
    <option disabled value="" selected="selected">Please select one</option>
    <option v-if="options== 'country'" v-for="i in items" v-bind:value="i">{{i["noc"]}}</option>
    <option v-if="options == 'event'" v-for="i in items" v-bind:value="i">{{i["event"]}}</option>

  </select>
</template>

<script>

import {api_request, Services} from "@/requests.js"

export default { 
  props: {
    options: {
      type: String, 
      required: true
    }
  },
  data() {
    return {
        items: null,
        item: ""
    };
  }, 
  mounted() {
    this.load_items();
  },
  methods: {
    async load_items() {
        if(this.options == "country") {
          this.items = await api_request(Services.regions_table);
        }
        else if(this.options == "event") {
          this.items = await api_request(Services.event_table);
        }
    },
    onChange(event) {
      if(this.item["noc"] != undefined) {
        this.$emit('countryChange', this.item["noc"]);  
      }
      else if(this.item["event"] != undefined) {
        this.$emit('eventChange', this.item["event"]);  
      }
    }
  }
}
</script>

<style scoped>
  @import "bootstrap";
</style>