<template>
  <div class="table-filters-ctn">
    <div class="select-ctn">
      <p class="select-label">Établissement</p>
      <el-select v-model="selectValue" placeholder="Select">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value">
        </el-option>
      </el-select>
    </div>
    <div class="dates-ctn">
      <p>du</p>
      <el-date-picker v-model="dateFrom"></el-date-picker>
      <p>au</p>
      <el-date-picker v-model="dateTo"></el-date-picker>
      <el-button>
        <i class="el-icon-search"></i>
      </el-button>
    </div>
    <div class="action-buttons-ctn">
      <el-button>Imprimer</el-button>
      <el-button>Exporter</el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TableFilters',
  data() {
    return {
      selectValue: 'EHPAD DU LAC',
      dateFrom: 'Sun Dec 02 2019 00:00:00 GMT+0200 (heure d’été d’Europe centrale)',
      dateTo: 'Thu Jan 02 2020 00:00:00 GMT+0200 (heure d’été d’Europe centrale)',
      options: [{
        value: 'ehpadDuLac',
        label: 'EHPAD DU LAC'
      }, {
        value: 'ehpad2',
        label: 'EHPAD 2'
      }, {
        value: 'ehpad3',
        label: 'EHPAD 3'
      }, {
        value: 'ehpad4',
        label: 'EHPAD 4'
      }, {
        value: 'ehpad5',
        label: 'EHPAD 5'
      }],
      value: ''
    }
  }
}
</script>

<style>
.table-filters-ctn {
  background: rgb(240, 247, 249);
  height: 120px;
  width: 90%;
  margin: 20px 0 50px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  border-radius: 7px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  border: 2px solid rgb(213, 232, 233);
}

.select-ctn {
  text-align: left;
}

.select-label {
  margin: 0 0 10px 0;
}

.dates-ctn {
  display: flex;
  align-items: center;
}

.el-date-editor {
  margin: 0 10px;
}
</style>