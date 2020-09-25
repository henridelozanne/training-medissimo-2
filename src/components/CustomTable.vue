<template>
  <div class="section">
    <h1 class="stat-header-ctn">
      <i class="el-icon-s-data stat-icon"></i>
      <span>Statistiques</span>
      <i class="el-icon-right arrow-icon"></i>
      <span>{{ header }}</span>
    </h1>

    <div class="stat-subheader-ctn">
      <h2>{{ subheader }}</h2>
      <el-button>
        <i class="el-icon-back"></i>
        <span>Retour</span>
      </el-button>
    </div>

    <TableFilters />

    <el-table border
              :data="tableData"
              show-summary
              :sum-text="'Total 12 mois'"
              height="100">
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
    header: { type: String, default: '' },
    subheader: { type: String, default: '' },
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
.stat-subheader-ctn {
  width: 90%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.el-table {
  width: 90%;
  flex-grow: 1;
  margin-bottom: 80px;
}
</style>