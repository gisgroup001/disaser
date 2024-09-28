<template>
  <div id="container" style="height: 300px; width: 100%"></div>
</template>

<script>
import * as echarts from 'echarts';

export default {
  name: 'chart1',
  mounted() {
    this.initChart();
    window.addEventListener('resize', this.chartResize);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.chartResize);
    if (this.myChart) {
      this.myChart.dispose();
    }
  },
  methods: {
    initChart() {
      const dom = document.getElementById('container');
      this.myChart = echarts.init(dom);

      const data = [
        {
          name: '地震',
          itemStyle: {
            color: '#da1d23'
          },
          children: [
            {
              name: '山东',
              itemStyle: {
                color: '#dd4c51'
              },
              children: [
                {
                  name: '伤亡人数',
                  value: 1,
                  itemStyle: {
                    color: '#3e0317'
                  }
                },
                {
                  name: '发生时间',
                  value: 1,
                  itemStyle: {
                    color: '#3e0317'
                  }
                }
              ]
            },
            {
              name: '四川',
              itemStyle: {
                color: '#da4c51'
              },
              children: [
                {
                  name: '伤亡人数',
                  value: 3,
                  itemStyle: {
                    color: '#ba1317'
                  }
                },
                {
                  name: '发生时间',
                  value: 1,
                  itemStyle: {
                    color: '#ff5733'
                  }
                },
                {
                  name: '震级',
                  value: 6.5,
                  itemStyle: {
                    color: '#c70039'
                  }
                }
              ]
            },
            {
              name: '云南',
              itemStyle: {
                color: '#ff7f50'
              },
              children: [
                {
                  name: '伤亡人数',
                  value: 2,
                  itemStyle: {
                    color: '#900c3f'
                  }
                },
                {
                  name: '发生时间',
                  value: 1,
                  itemStyle: {
                    color: '#581845'
                  }
                },
                {
                  name: '震级',
                  value: 5.8,
                  itemStyle: {
                    color: '#ffc300'
                  }
                }
              ]
            },
            {
              name: '河北',
              itemStyle: {
                color: '#ffcccb'
              },
              children: [
                {
                  name: '伤亡人数',
                  value: 5,
                  itemStyle: {
                    color: '#d2691e'
                  }
                },
                {
                  name: '发生时间',
                  value: 1,
                  itemStyle: {
                    color: '#8b4513'
                  }
                },
                {
                  name: '震级',
                  value: 4.9,
                  itemStyle: {
                    color: '#f4a460'
                  }
                }
              ]
            },
            {
              name: '新疆',
              itemStyle: {
                color: '#8b0000'
              },
              children: [
                {
                  name: '伤亡人数',
                  value: 0,
                  itemStyle: {
                    color: '#7f0000'
                  }
                },
                {
                  name: '发生时间',
                  value: 1,
                  itemStyle: {
                    color: '#ff4500'
                  }
                },
                {
                  name: '震级',
                  value: 6.0,
                  itemStyle: {
                    color: '#a52a2a'
                  }
                }
              ]
            }
          ]
        }
      ];


      const option = {
        series: {
          type: 'sunburst',
          data: data,
          radius: [0, '95%'],
          sort: undefined,
          emphasis: {
            focus: 'ancestor'
          },
          levels: [
            {},
            {
              r0: '15%',
              r: '35%',
              itemStyle: {
                borderWidth: 2
              },
              label: {
                rotate: 'tangential'
              }
            },
            {
              r0: '35%',
              r: '70%',
              label: {
                align: 'right'
              }
            },
            {
              r0: '70%',
              r: '75%',
              label: {
                position: 'outside',
                padding: 3,
                silent: false
              },
              itemStyle: {
                borderWidth: 3
              }
            }
          ]
        }
      };

      this.myChart.setOption(option);
    },
    chartResize() {
      if (this.myChart) {
        this.myChart.resize();
      }
    }
  }
};
</script>

<style scoped>
#container {
  height: 300px;
}
</style>
