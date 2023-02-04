
<template>
  <DataTable class="table table−hover table−striped" width="100%" :data="medals">
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
DataTable.use(DataTablesLib)
export default {
  components: {
    DataTable
  }, 
  data() {
    return {
      columns: ["Name", "Count"],
      medals: [[ "Bronze", 6553],
              [ "Gold", 6329 ],
              [ "Silver", 6269 ]]
    }
  }
}
</script>

<style scoped>
  @import "bootstrap";
  @import "datatables.net-bs5";
</style>