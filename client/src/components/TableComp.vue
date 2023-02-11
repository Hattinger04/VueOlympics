
<template>
  <DataTable v-if="values != undefined" class="table table−hover table−striped" width="100%" :data="values">
    <thead>
      <tr>
        <th v-for="c in columns">{{ c }} </th>
      </tr>
    </thead>
    <tfoot>
    </tfoot>
  </DataTable>
</template>

<script>
import DataTable from "datatables.net-vue3";
import DataTablesLib from 'datatables.net-bs5'
import {api_request_parameter, Services} from "@/requests.js"

DataTable.use(DataTablesLib)
export default {
  components: {
    DataTable
  },
  props: {
    options: {
      type: Object, 
      required: true
    }
  },
  data() {
    return {
      columns: [],
      values: undefined,
      event: "",
      country: ""
    }
  },
  watch: {
    options() {
      this.country = this.options["country"]; 
      this.event = this.options["event"];
      this.load_table()
    }
  },
  methods: {
    async load_table() {
      if(this.country != "") {
        this.columns = ["Name", "Count"]
        this.values = await api_request_parameter(Services.medals_table, this.country);
      }
    }
  }
}
</script>

<style scoped>
  @import "bootstrap";
  @import "datatables.net-bs5";
</style>