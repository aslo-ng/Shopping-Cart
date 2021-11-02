<template>
  <div class="home">
     <div id="pieContatiner" style="width:100%; height:400px">

     </div>
     <div id="clumnContaion" style="width:100%; height:400px"></div>
  </div>
</template>

<script type="text/javascript">
import * as Highcharts from 'highcharts';//as:重命名
 export default{
     name:'Home',
     methods:{
       pieFn(){
          Highcharts.chart('pieContatiner',{
          title: {
              text: '舆情关键词分布图'
          },
          tooltip: {
              pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
          },
          plotOptions: {
              pie: {
                  allowPointSelect: true,
                  cursor: 'pointer',
                  dataLabels: {
                      enabled: true,
                      format: '<b>{point.name}</b>: {point.percentage:.1f} %',
                      style: {
                          color: (Highcharts.theme && Highcharts.theme.contrastTextColor) || 'black'
                      },
                      connectorColor: 'silver'
                  }
              }
          },
          series: [{
              type: 'pie',
              name: '舆情分布',
              data: [
                  {
                    name:'天然气分公司',  
                    y: 18.2,
                    sliced: true,
                    selected: true
                  },
                  ['大庆石油',       32.1],
                  ['延长石油', 22.6],
                  ['中国石油',    27.0],
              ]
          }]
      });
       },
     },
     mounted(){
       this.pieFn();
     }
}
</script>

<style>
#datatable {
    border: 1px solid #ccc;
    border-collapse: collapse;
    border-spacing: 0;
    font-size: 12px;
}
td,th {
    border: 1px solid #ccc;
    padding: 4px 20px;
}
</style>
