<template>
  <div>
     <div id="myChart"></div>
  </div>
</template>
<script>
  /*
  // 引入基本模板
  let echarts = require('echarts/lib/echarts')
  // 引入柱状图组件
  require('echarts/lib/chart/bar')
  // 引入提示框和title组件
  require('echarts/lib/component/tooltip')
  require('echarts/lib/component/title')
  */
  export default {
    name:'index',
    data() {
      return {
         option:{
           tooltip : {
             trigger: 'axis',
             axisPointer : {            // 坐标轴指示器，坐标轴触发有效
               type : 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
             }
           },

           legend: {
             data:['冰箱','彩电','空调','洗衣机']
           },
           toolbox: {
             show : true,
             orient: 'vertical',
             x: 'right',
             y: 'center',
             feature : {
               mark : {show: true},
               dataView : {show: true, readOnly: false},
               magicType : {show: true, type: ['line', 'bar', 'stack', 'tiled']},
               restore : {show: true},
               saveAsImage : {show: true}
             }
           },
           calculable : true,
           xAxis : [
             {
               type : 'category',
               data : ['3月','4月','5月','6月','7月','8月','9月']
             }
           ],
           yAxis : [
             {
               type : 'value'
             }
           ],
           series : [
             {
               name:'冰箱',
               type:'bar',
               data:[320, 332, 301, 334, 390, 330, 320]
             },
             {
               name:'彩电',
               type:'bar',
               stack: '广告',
               data:[120, 132, 101, 134, 90, 230, 210]
             },
             {
               name:'空调',
               type:'bar',
               stack: '广告',
               data:[220, 182, 191, 234, 290, 330, 310]
             },
             {
               name:'洗衣机',
               type:'bar',
               stack: '广告',
               data:[150, 232, 201, 154, 190, 330, 410]
             }
           ]
         }
      }
    },
    computed:{

    },
    methods:{
       drawSaleCondition(){
         var vm=this;
         var myChart=vm.$echarts.init(document.getElementById('myChart'));
         myChart.setOption(vm.option)
         //实现echarts图表的自适应
         window.addEventListener("resize", () => { myChart.resize();});
       }
    },
    mounted(){
      var vm=this;
      //发起网络请求获取图表数据
      //首页加载 销售情况图
      vm.drawSaleCondition();
    }
  }
</script>
<style lang="less" rel="stylesheet/less">
   @border:1px solid green;
  #myChart{
    width:90%;
    height:400px;
    margin:20px auto;
  }
</style>
