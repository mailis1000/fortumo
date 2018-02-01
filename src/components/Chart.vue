<script>
/* eslint-disable */
import {Bar} from 'vue-chartjs'
import { Line } from 'vue-chartjs'
import 'chartjs-plugin-annotation'

import json from './../assets/data.json'

export default {
  name: 'chart',
  extends: Line,
  data () {
    return {
      datacollection: {
        labels: [],
        datasets: [
          {
            label: 'Months',
            data: [],
            borderColor: 'rgba(232, 57, 46, 1)',
            backgroundColor: 'rgba(232, 57, 46, 0.5)'
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          yAxes: [{
            ticks: {
              beginAtZero: true,
              fontColor: '#fff',
              fontSize: 22,
              padding: 20
            },
            gridLines: {
              color: '#474646'
            }
          }],
          xAxes: [{
            ticks: {
              fontColor: '#fff',
              fontSize: 30,
              maxRotation: 90,
              minRotation: 90,
              padding: 20
            },
            gridLines: {
              color: '#474646'
            }
          }]
        },
        legend: {
          display: false
        },
        layout: {
          padding: {
            left: 50,
            right: 100
          }
        },
        annotation: {
          annotations: [{
              type: 'line',
              mode: 'horizontal',
              scaleID: 'y-axis-0',
              value: json.gtv.endOfYearTarget,
              borderColor: '#189c00',
              borderWidth: 2
          }],
          drawTime: "afterDraw" // (default)
        }
      }
    }
  },
  mounted () {
    this.createData()
    this.renderChart(this.datacollection, this.options)
  },
  methods: {
    createData () {
      let i = 0;
      for (i = 0; i < json.gtv.results.length; i++) { 
        this.datacollection.datasets[0].data.push([json.gtv.results[i]])
        this.datacollection.labels.push(json.months[i])
      }
      // for (i = 0; i < json.gtv.results.length; i++) { 
      //   this.datacollection.datasets[i] = {
      //     label: json.months[i],
      //     data: [json.gtv.results[i]]
      //     }
      //   this.datacollection.labels.push(json.months[i])
      // }
    }
  }
}
</script>
