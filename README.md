English | [简体中文](./README.zh-CN.md)



# markdown-it-charts



> Chart plugin for markdown-it. Fast and easy to extend markdown-it.
> support chart.js、echarts、highcharts、CHARTIST、c3.js、tauCharts.



## Install

node.js & bower:

```
npm install markdown-it-charts --save
bower install markdown-it-charts --save
```



## Usage examples

### chat.js

**node.js**

> token.info is **chart**

```js
var markdownIt = require("markdown-it");
var markdownItCharts = require("markdown-it-charts");
const md = new markdownIt();
md.use(markdownItCharts);
md.render(`\`\`\`chart
{
  "type": "pie",
  "data": {
    "labels": [
      "Red",
      "Blue",
      "Yellow"
    ],
    "datasets": [
      {
        "data": [
          300,
          50,
          100
        ],
        "backgroundColor": [
          "#FF6384",
          "#36A2EB",
          "#FFCE56"
        ],
        "hoverBackgroundColor": [
          "#FF6384",
          "#36A2EB",
          "#FFCE56"
        ]
      }
    ]
  },
  "options": {}
}
\`\`\``);
```

**Browser**

```js
<script type="text/javascript"src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script type="text/javascript"src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.7.2/Chart.bundle.min.js"></script>
<script>
  $(function(){
        var reg = /^[\'\"]+|[\'\"]+$/g;
         //-  chart.js
        var chartjsLen = $('.chartjs').length;
        var myChartJs = [];
        for(var i = 0;i < chartjsLen; i++){
            var ctx = $('.chartjs')[i].getContext('2d');
            myChartJs[i] = new Chart(ctx,$.parseJSON($($('.chartjs')[i])[0].innerHTML))
        }
  })
</script>
```

[Documentation for charts](https://chartjs.bootcss.com/)

### echarts

**node.js**

> token.info is **echarts**

```js
var markdownIt = require("markdown-it");
var markdownItCharts = require("markdown-it-charts");
const md = new markdownIt();
md.use(markdownItCharts);
md.render(`\`\`\`echarts
{
    "option": {
        "xAxis": {
            "type": "category",
            "data": [
                "Mon",
                "Tue",
                "Wed",
                "Thu",
                "Fri",
                "Sat",
                "Sun"
            ]
        },
        "yAxis": {
            "type": "value"
        },
        "series": [
            {
                "data": [
                    820,
                    932,
                    901,
                    934,
                    1290,
                    1330,
                    1320
                ],
                "type": "line"
            }
        ]
    }
}
\`\`\``);
```


**Browser**

```js
<script type="text/javascript"src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script src="https://cdn.bootcss.com/echarts/4.1.0.rc2/echarts.min.js"></script>
<script>
  $(function(){
        var reg = /^[\'\"]+|[\'\"]+$/g
       //- echarts
        var echartsLen = $('.echarts').length;
        var echartsChart = [];
        var echartsOption = [];
        for(var j = 0;j < echartsLen;j++){
            echartsChart[j] = echarts.init($('.echarts')[j]);
            echartsOption[j] = $.parseJSON($($('.echarts-data')[j])[0].innerHTML).option;
            echartsChart[j].setOption(echartsOption[j]);
        }
  })
</script>
```

[Documentation for echarts](http://echarts.baidu.com/api.html#echarts)

### CHARTIST

**node.js**

> token.info is **chartist**

```js
var markdownIt = require("markdown-it");
var markdownItCharts = require("markdown-it-charts");
const md = new markdownIt();
md.use(markdownItCharts);
md.render(`\`\`\`chartist
{
    "chartist":{
        "data":{
            "labels": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
            "series": [
                [12, 9, 7, 8, 5],
                [2, 1, 3.5, 7, 3],
                [1, 3, 4, 5, 6]
            ]
        }, 
        "options":{
            "fullWidth": true,
            "chartPadding": {
            "right": 40
            }
    }
}
\`\`\``);
```


**Browser**

```js
<link href="https://cdn.bootcss.com/chartist/0.11.0/chartist.min.css" rel="stylesheet">
<script type="text/javascript" src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script type="text/javascript" src="https://cdn.bootcss.com/chartist/0.11.0/chartist.min.js"></script>
<script>
  $(function(){
        var reg = /^[\'\"]+|[\'\"]+$/g
       //-  chartist
         var charistLen = $('.ct-chart').length;
         for(var m = 0;m < charistLen; m++){
            var temp = $.parseJSON($($('.chartist-data')[m])[0].innerHTML)
            new Chartist.Line($($('.ct-chart')[m])[0],temp.data,temp.option);
         }
  })
</script>
```

[Documentation for chartist](https://gionkunz.github.io/chartist-js/api-documentation.html)

### c3.js

**node.js**

> token.info is **c3**
>
> unique id is required

```javascript
var markdownIt = require("markdown-it");
var markdownItCharts = require("markdown-it-charts");
const md = new markdownIt();
md.use(markdownItCharts);
md.render(`\`\`\`c3
{
	"id":"c3-1",
    "data": {
        "columns": [
            ["sample", 30, 200, 100, 400, 150, 250]
        ]
    },
    "axis": {
        "y": {
            "max": 400,
            "min": -400
        }
    }
}
\`\`\``);
```

**Browser**

```javascript
<link href="https://cdn.bootcss.com/c3/0.6.1/c3.min.css" rel="stylesheet">
<script type="text/javascript" src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
// c3.js is rely on d3.js
<script type="text/javascript" src="https://cdn.bootcss.com/d3/4.13.0/d3.min.js"></script>
<script type="text/javascript" src="https://cdn.bootcss.com/c3/0.6.1/c3.js"></script>
<script>
  $(function(){
        var reg = /^[\'\"]+|[\'\"]+$/g
        //-  c3.js
        var c3ChartLen = $('.c3-chart').length;
        var c3Chart = [];
        for(var n = 0;n < c3ChartLen; n++){
            var temp = $.parseJSON($($('.c3-data')[n])[0].innerHTML);
            c3Chart[n] = c3.generate({
                bindto:document.getElementById(temp.id),
                data:temp.data,
                axis:temp.axis,
                grid:temp.grid,
                regions:temp.regions,
                legend:temp.legend,
                tooltip:temp.tooltip,
                subchart:temp.subchart,
                zoom:temp.zoom,
                point:temp.point,
                line:temp.line,
                area:temp.area,
                bar:temp.bar,
                pie:temp.pie,
                donut:temp.donut,
                gauge:temp.gauge,
            })
        }
  })
</script>
```

[Documentation for C3.js](http://c3js.org/)

### tauCharts

**node.js**

> token.info is **c3**

> unique id is required

```javascript
var markdownIt = require("markdown-it");
var markdownItCharts = require("markdown-it-charts");
const md = new markdownIt();
md.use(markdownItCharts);
md.render(`\`\`\`taucharts
{
    "id":"tauchartsid-1",
    "type": "stacked-area",
    "x": "date",
    "y": "effort",
    "color": "team",
    "data": [
        {"team": "Alpha", "date": "2015-07-15", "effort": 400},
        {"team": "Alpha", "date": "2015-07-16", "effort": 200},
        {"team": "Alpha", "date": "2015-07-17", "effort": 300},
        {"team": "Alpha", "date": "2015-07-18", "effort": 500},
        {"team": "Beta",  "date": "2015-07-15", "effort": 100},
        {"team": "Beta",  "date": "2015-07-16", "effort": 200},
        {"team": "Beta",  "date": "2015-07-17", "effort": 300},
        {"team": "Beta",  "date": "2015-07-18", "effort": 100},
        {"team": "Gamma", "date": "2015-07-15", "effort": 300},
        {"team": "Gamma", "date": "2015-07-16", "effort": 100},
        {"team": "Gamma", "date": "2015-07-17", "effort": 100},
        {"team": "Gamma", "date": "2015-07-18", "effort": 200}
    ]
}
\`\`\``);
```

**Browser**

```javascript
<link href="http://cdn.jsdelivr.net/npm/taucharts@2/dist/taucharts.min.css" rel="stylesheet">
<script type="text/javascript" src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script type="text/javascript" src="//cdn.jsdelivr.net/d3js/latest/d3.min.js"></script>
<script type="text/javascript" src="//cdn.jsdelivr.net/npm/taucharts@2/dist/taucharts.min.js"></script>
// taucharts.js is rely on d3.js
// the latest taucharts.js is rely on D3.js V4. please see the documents of taucharts.js.
<script>
  $(function(){
        var reg = /^[\'\"]+|[\'\"]+$/g
        //- taucharts
        var tauchartsLen = $('.taucharts').length;
        var taucharts = [];
        for(var v=0;v<tauchartsLen;v++){
            var temp = $.parseJSON($($('.taucharts-data')[n])[0].innerHTML);
            console.log(temp);
            taucharts[v] =  new Taucharts.Chart(
               temp
            )
            taucharts[v].renderTo(document.getElementById(temp.id));
        }
  })
</script>
```

[Documentation for tauCharts](https://www.taucharts.com/)



###  Contributing

If you have a bug or an idea,  open issues [here](https://github.com/chuyun/markdown-it-charts/issues)