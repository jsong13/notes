```javascript
optcommon = {
    xAxis: {
      type: 'datetime',
      crosshair: true,
    },
    yAxis: {
      crosshair: true,
    },  
    tooltip: {
      xDateFormat: '%H:%m:%S',
      shared : true,
      valueDecimals: 2,
    },
    credits:{
      enabled : false,
    },
    time: {
        timezone: 'America/New_York'
    },
    title : undefined,
    yAxis:[
      {title:undefined,opposite:false},
      {title:undefined,opposite:true},
    ],

}

document.addEventListener('DOMContentLoaded', function () {
  var opt1 = {
    data : {
      csvURL: window.location.origin + '/app1.csv',
      itemDelimiter: "\t",
      dataRefreshRate: 15,
      enablePolling:true,
      complete : function(o){
        o.series = [o.series[0],o.series[1],]
        o.series[1].yAxis=0
      },
    },
  }
  var chart1 = Highcharts.chart('fig1', Object.assign({}, optcommon, opt1)) 
  
  
  var opt2 = {
    data : {
      csvURL: window.location.origin + '/app1.csv',
      itemDelimiter: "\t",
      dataRefreshRate: 11,
      enablePolling:true,
      complete : function(o){
        o.series = [o.series[2],o.series[3],]
        window.debug = o
        document.getElementById("header2").innerHTML = '<h3>'+o.series[0].data.length+'</h3>'
      },
    },
  }
  var chart1 = Highcharts.chart('fig2', Object.assign({}, optcommon, opt2)) 
  
});

```
