<template>
  <div class="section">
    <h1>{{ title }}</h1>

    <TableFilters />

    <el-table border
              :data="tableData"
              style="width: 100%"
              show-summary
              :sum-text="'Total 12 mois'">
      <el-table-column prop="year" label="Année" width="130" />
      <el-table-column prop="month" label="Mois" width="120" />
      <el-table-column prop="totalCa" label="Chiffre d'affaires total" :formatter="formatter" />
      <el-table-column prop="patientQty" label="Nombre de patients"  />
      <el-table-column prop="prescriptionQty" label="Nombre de prescriptions" >
        <template slot-scope="scope">
          <span style="margin-right: 10px">{{ scope.row.prescriptionQty }}</span>
          <i :class="scope.row.prescriptionQty < 10 ? 'el-icon-bottom-right' : 'el-icon-top-right'"
             :style="scope.row.prescriptionQty < 10 ? 'color: red' : 'color: green'"></i>
        </template>
      </el-table-column>
      <el-table-column prop="nonReconditionedCA" label="CA non reconditionné" :formatter="formatter"  />
      <el-table-column prop="reconditionedCA" label="CA reconditionné" :formatter="formatter" />
      <el-table-column prop="mono28" label="mono28"  />
      <el-table-column prop="medipac" label="medipac"  />
    </el-table>
  </div>
</template>

<script>
import TableFilters from './TableFilters';

export default {
  name: 'CustomTable1',
  components: {
    TableFilters
  },
  props: {
    title: { type: String, default: '' },
    tableData: { type: Array, default: () => []}
  },
  methods: {
    formatter(row, col) {
      if (col.property === 'totalCa') {
        return row.totalCa + '€'
      } else if (col.property === 'nonReconditionedCA') {
        return row.nonReconditionedCA + '€'
      } else if (col.property === 'reconditionedCA') {
        return row.reconditionedCA + '€'
      }
    },
  },
};
</script>

<style>

</style>