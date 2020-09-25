<template>
  <div id="app">
    <CustomTable :header="customTable.header"
                 :subheader="customTable.subheader"
                 :tableData="customTable.tableData" />
    <StackedColumn
        :id="stackedColumn.id"
        :data="stackedColumn.data"
        :title="stackedColumn.title" />
    <Lines :id="lines.id"
           :title="lines.title"
           :data="lines.data" />
    <PieChart
        :title="first.title"
        :data="first.data"
        :id="first.id"
        :emptyCenter="first.emptyCenter"
        :bottomInfo="first.bottomInfo" />
    <PieChart
        :title="second.title"
        :data="second.data"
        :id="second.id"
        :emptyCenter="second.emptyCenter"
        :bottomInfo="second.bottomInfo" />
    <PieChart
        :title="patients.title"
        :data="patients.data"
        :id="patients.id"
        :emptyCenter="patients.emptyCenter"
        :bottomInfo="patients.bottomInfo" />
    <PieChart
        :title="prescriptions.title"
        :data="prescriptions.data"
        :id="prescriptions.id"
        :emptyCenter="prescriptions.emptyCenter"
        :bottomInfo="prescriptions.bottomInfo" />
    <PieChart
        :title="piluliers.title"
        :data="piluliers.data"
        :id="piluliers.id"
        :emptyCenter="piluliers.emptyCenter"
        :bottomInfo="piluliers.bottomInfo" />
  </div>
</template>

<script>
import CustomTable from './components/CustomTable'
import PieChart from './components/PieChart'
import StackedColumn from './components/StackedColumn'
import Lines from './components/Lines'

export default {
  name: 'App',
  components: {
    CustomTable,
    PieChart,
    Lines,
    StackedColumn
  },
  data() {
    return {
      customTable: {
        header: 'Chiffre d\'affaires',
        subheader: 'Évolution détaillée de l\'activité PDA',
        tableData: [{
            year: '2020',
            month: '01',
            totalCa: '4950.58',
            patientQty: '81',
            prescriptionQty: '32',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '02',
            totalCa: '1350.21',
            patientQty: '32',
            prescriptionQty: '22',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '03',
            totalCa: '2950.92',
            patientQty: '23',
            prescriptionQty: '4',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '04',
            totalCa: '750.47',
            patientQty: '831',
            prescriptionQty: '3',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '05',
            totalCa: '6250.74',
            patientQty: '87',
            prescriptionQty: '77',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '06',
            totalCa: '3950.58',
            patientQty: '12',
            prescriptionQty: '63',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '07',
            totalCa: '1950.32',
            patientQty: '14',
            prescriptionQty: '32',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '08',
            totalCa: '7352.23',
            patientQty: '24',
            prescriptionQty: '3',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '09',
            totalCa: '4950.42',
            patientQty: '53',
            prescriptionQty: '4',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '10',
            totalCa: '3672.77',
            patientQty: '7',
            prescriptionQty: '72',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '11',
            totalCa: '2738.33',
            patientQty: '81',
            prescriptionQty: '12',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }, {
            year: '2020',
            month: '12',
            totalCa: '8723.58',
            patientQty: '73',
            prescriptionQty: '10',
            nonReconditionedCA: '2523.97',
            reconditionedCA: '1524.23',
            mono28: '815',
            medipac: '16'
          }]
      },
      lines: {
        id: 'lines-chart',
        title: 'Substitutions',
        data: [{
          date: new Date('July 1, 2019 00:00:00'),
          value: 3000,
        }, {
          date: new Date('August 1, 2019 00:00:00'),
          value: 3100,
        }, {
          date: new Date('September 1, 2019 00:00:00'),
          value: 3300,
        }, {
          date: new Date('October 1, 2019 00:00:00'),
          value: 3150,
        }, {
          date: new Date('November 1, 2019 00:00:00'),
          value: 3300,
        }, {
          date: new Date('December 1, 2019 00:00:00'),
          value: 3600,
        }, {
          date: new Date('January 1, 2020 00:00:00'),
          value: 3400,
        }, {
          date: new Date('February 1, 2020 00:00:00'),
          value: 3700,
        }, {
          date: new Date('March 1, 2020 00:00:00'),
          value: 3800,
        }, {
          date: new Date('April 1, 2020 00:00:00'),
          value: 3900,
        }, {
          date: new Date('May 1, 2020 00:00:00'),
          value: 4000,
        }, {
          date: new Date('June 1, 2020 00:00:00'),
          value: 4100,
        }]
      },
      stackedColumn: {
        id: 'stack-ca',
        title: 'Chiffre d\'affaires',
        data: [
                {
                  "month": 'jan',
                  "pilulier": 2.5,
                  "boite": 2.5,
                }, {
                  "month": 'fev',
                  "pilulier": 2.6,
                  "boite": 2.7,
                }, {
                  "month": 'mar',
                  "pilulier": 2.8,
                  "boite": 2.9,
                }, {
                  "month": 'avr',
                  "pilulier": 2.5,
                  "boite": 2.5,
                }, {
                  "month": 'mai',
                  "pilulier": 2.6,
                  "boite": 2.7,
                }, {
                  "month": 'jun',
                  "pilulier": 2.8,
                  "boite": 2.9,
                }, {
                  "month": 'jul',
                  "pilulier": 2.5,
                  "boite": 2.5,
                }, {
                  "month": 'fev',
                  "pilulier": 2.6,
                  "boite": 2.7,
                }, {
                  "month": 'aou',
                  "pilulier": 2.8,
                  "boite": 2.9,
                }, {
                  "month": 'sep',
                  "pilulier": 2.5,
                  "boite": 2.5,
                }, {
                  "month": 'oct',
                  "pilulier": 2.6,
                  "boite": 2.7,
                }, {
                  "month": 'nov',
                  "pilulier": 2.8,
                  "boite": 2.9,
                }, {
                  "month": 'dec',
                  "pilulier": 2.8,
                  "boite": 2.9,
                }
    ]
      },
      first: {
        emptyCenter: false,
        title: 'Chiffre d\'affaires',
        id: 'ca',
        data: [{
          category: "Piluliers",
          value: 60
        }, {
          category: "Boîtes",
          value: 40
        }],
        bottomInfo: 'CA Total: 63 132€'
      },
      second: {
        emptyCenter: false,
        title: 'Substitutions',
        id: 'substitutions',
        data: [{
          category: "Princeps",
          value: 71
        }, {
          category: "Génériques",
          value: 25
        }, {
          category: "Princeps substituables",
          value: 4
        }]
      },
      patients: {
        emptyCenter: true,
        title: 'Patients',
        id: 'patients',
        data: [{
          category: 'Hommes',
          value: 38
        }, {
          category: 'Femmes',
          value: 90
        }],
        bottomInfo: 'Age moyen: 79 ans'
      },
      prescriptions: {
        emptyCenter: true,
        title: 'Prescriptions',
        id: 'prescriptions',
        data: [{
          category: 'Medipac',
          value: 52
        }, {
          category: 'Mono28',
          value: 1506
        }],
        bottomInfo: 'Moyenne: 1, 2 prescriptions/patient/mois'
      },
      piluliers: {
        emptyCenter: true,
        title: 'Piluliers',
        id: 'piluliers',
        data: [{
          category: 'Medipac',
          value: 208
        }, {
          category: 'Mono28',
          value: 9789
        }],
        bottomInfo: 'Moyenne: 6,1 pilulier/patient/mois'
      }
    };
  },
}
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.section {
  height: 100vh;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
}

.section h2 {
  margin-bottom: 0;
}

.stat-header-ctn {
  width: 90%;
  text-align: left;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-top: 0;

  .stat-icon {
    margin-right: 10px;
  }

  .arrow-icon {
    margin: 0 10px;
  }
}
</style>
