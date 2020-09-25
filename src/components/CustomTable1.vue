<template>
  <div class="section">
    <h1 style="margin-bottom: 100px">First table</h1>
    <el-table border
              height="500"
              :row-class-name="tableRowClassName"
              :data="tableData"
              style="width: 100%"
              >
      <el-table-column fixed sortable prop="date" label="Date" width="180"
                       :filters="[{text: '2016-05-01', value: '2016-05-01'}, {text: '2016-05-02', value: '2016-05-02'}, {text: '2016-05-03', value: '2016-05-03'}, {text: '2016-05-04', value: '2016-05-04'}]"
                       :filter-method="filterHandler">
      </el-table-column>
      <el-table-column sortable prop="name" label="Name" width="180" :formatter="formatter">
      </el-table-column>
      <el-table-column prop="address" label="Address">
        <template slot-scope="scope">
          <i class="el-icon-top-right" style="color: green"></i>
          <span style="margin-left: 10px">{{ scope.row.date }}</span>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'CustomTable1',
  props: {
    title: { type: String, default: '' },
  },
  data() {
    return {
      tableData: [{
            date: '2016-05-03',
            name: 'Chantal',
            address: 'No. 189, Grove St, Los Angelo'
          }, {
            date: '2016-05-02',
            name: 'Dimitri',
            address: 'No. 189, Grove St, Los Angeles'
          }, {
            date: '2016-05-04',
            name: 'Alfred',
            address: 'No. 189, Grove St, Los Angeles'
          }, {
            date: '2016-05-01',
            name: 'Stéphane',
            address: 'No. 189, Grove St, Los Angeles'
          }]
    }
  },
  methods: {
    /* eslint-disable-next-line */
    tableRowClassName({row, rowIndex}) {
      // console.log('row: ', row)
      if (rowIndex === 1) {
        return 'warning-row';
      } else if (rowIndex === 3) {
        return 'success-row';
      }
      return '';
    },
    filterHandler(value, row, column) {
      const property = column['property'];
      return row[property] === value;
    },
    formatter(row) {
      return row.name + ' *'
    }
  },
};
</script>

<style>
  .el-table .warning-row {
    background: oldlace;
  }

  .el-table .success-row {
    background: #f0f9eb;
  }
</style>