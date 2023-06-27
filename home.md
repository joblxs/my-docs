```dataviewjs
//计算本月有多少天,还剩多少天
let today = new Date()
let lastDayOfMonth = new Date(today.getFullYear(), today.getMonth() + 1, 0)
let remainingDays = lastDayOfMonth.getDate() - today.getDate() + 1 //还剩多少天
let totalDays = lastDayOfMonth.getDate() //本月天数

//计算倒计天数
let targetDate = new Date("2023-12-24")
let timeDiff = targetDate.getTime() - today.getTime()
let daysDiff = Math.floor(timeDiff / (1000 * 60 * 60 * 24)) //倒计天数

//设置日期&weekday输出格式
const weekday = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'][today.getDay()]
const formattedDate = `${today.getFullYear()}-${(today.getMonth() + 1).toString().padStart(2, '0')}-${today.getDate().toString().padStart(2, '0')} --${weekday}` 

//输出部分
dv.el('div', formattedDate);
dv.el('div','本月还剩'+remainingDays+'天')
dv.el('progress',null,{attr:{max:totalDays,value:remainingDays}} ) //进度条 1
dv.el('div','倒计还剩'+daysDiff+' /300天')
dv.el('progress',null,{attr:{max:300,value:daysDiff}}) //进度条2
```

```dataviewjs
dv.span("** 😊  😥**") /* optional ⏹️💤⚡⚠🧩↑↓⏳📔💾📁📝🔄📝🔀⌨️🕸️📅🔍✨ */
const calendarData = {
    year: 2023,  // (optional) defaults to current year
    colors: {    // (optional) defaults to green
        blue:        ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"], // first entry is considered default if supplied
        green:       ["#c6e48b", "#7bc96f", "#49af5d", "#2e8840", "#196127"],
        red:         ["#ff9e82", "#ff7b55", "#ff4d1a", "#e73400", "#bd2a00"],
        orange:      ["#ffa244", "#fd7f00", "#dd6f00", "#bf6000", "#9b4e00"],
        pink:        ["#ff96cb", "#ff70b8", "#ff3a9d", "#ee0077", "#c30062"],
        orangeToRed: ["#ffdf04", "#ffbe04", "#ff9a03", "#ff6d02", "#ff2c01"]
    },
    showCurrentDayBorder: true, // (optional) defaults to true
    defaultEntryIntensity: 4,   // (optional) defaults to 4
    intensityScaleStart: 10,    // (optional) defaults to lowest value passed to entries.intensity
    intensityScaleEnd: 100,     // (optional) defaults to highest value passed to entries.intensity
    entries: [],                // (required) populated in the DataviewJS loop below
}

//DataviewJS loop
for (let page of dv.pages('"/"').where(p => p.exercise)) {
    //dv.span("<br>" + page.file.name) // uncomment for troubleshooting
    calendarData.entries.push({
        date: page.file.name,     // (required) Format YYYY-MM-DD
        intensity: page.exercise, // (required) the data you want to track, will map color intensities automatically
        content: "🏋️",           // (optional) Add text to the date cell
        color: "orange",          // (optional) Reference from *calendarData.colors*. If no color is supplied; colors[0] is used
    })
}

renderHeatmapCalendar(this.container, calendarData)
```

 ```dataviewjs
let nofold = ''
let ftMd = dv.pages("").file.sort(t => t.mday)[0]
let total = parseInt([new Date() - ftMd.ctime] / (60*60*24*1000))
let allFile = dv.pages(nofold).file
dv.paragraph(`
>[!note|noicon] ## Ob天数 [[echarts-笔记动态显示-分布|${total}]]
>
`)
```


<iframe scrolling="no" src="https://v2.jinrishici.com/one.svg?font-size=28&spacing=2&color=bleak" frameborder="0" width="500" height="30" allowtransparency="true"></iframe>


```dataviewjs
const echarts = app.plugins.plugins['obsidian-echarts'].echarts()
let pages= dv.pages()
	           .groupBy(p => p.file.mday.toFormat("yyyy-MM:dd"))
           .map(p => ({cday: p.key , count: p.rows.length,wordcout:p.rows.values}))
           .array();
  function sumItem(arr1, arr2) {
            if (arr2.length == 0) {
                return arr1;
            } else {
                arr1.map(function(value, index) {
                    arr2[index] += value;
                })
            }
            return arr2;
        }

const xData = []
const yData = []
const y2Data = [] 
pages.forEach((page)=>{
	xData.push(page.cday)
	yData.push(page.count)
	y2Data.push(page.wordcout)
})
 let wordscout=[]
 let num =0
	for (let i = 0; i < y2Data.length; i++) {
		for (let j = 0; j < y2Data[i].length; j++) {
				num+=Number(y2Data[i][j].file.size)	
		}
	wordscout[i]=parseInt((num/3)/8)
	}
const y3Data =sumItem(yData,wordscout)
console.log(y2Data)

// Generate data
var category = xData;
var dottedBase = [];               
var barData = y3Data;
            

var dottedBase = [];
var lineData = yData;              

// option
const options = {
    backgroundColor: 'transparent',
         height: '300px',
    title: {
        text: '',
        x: 'center',
        y: 0,
        textStyle:{
            color:'#B4B4B4',
            fontSize:16,
            fontWeight:'normal',
        },
        
    },
    tooltip: {
        trigger: 'axis',
        backgroundColor:'rgba(255,255,255,0.8)',
        axisPointer: {
            type: 'shadow',
            label: {
                show: true,
                backgroundColor: '#7B7DDC'
            }
        }
    },
    legend: {
        data: ['笔记数量','笔记体积'],
        textStyle: {
            color: '#B4B4B4'
        },
        top:'3%',
    },
    grid:{
        // x:'12%',
        width:'95%',
        // y:'12%',
        left:"10%",
        // right:"30%",
        bottom:"60%"
        
    },
    xAxis: {
        data: category,
        axisLine: {
            lineStyle: {
                color: '#B4B4B4'
            }
        },
        axisTick:{
            show:false,
        },
    },
    yAxis: [{

        splitLine: {show: false},
        axisLine: {
            lineStyle: {
                color: '#B4B4B4',
            }
        },
        
        axisLabel:{
            formatter:'{value} ',
        }
    },
        {

        splitLine: {show: false},
        axisLine: {
            lineStyle: {
                color: '#B4B4B4',
            }
        },
        axisLabel:{
            formatter:'{value} ',
        }
    }],
    
    series: [{
        name: '笔记数量',
        type: 'line',
        smooth: true,
        showAllSymbol: true,
        symbol: 'emptyCircle',
        symbolSize: 8,
        yAxisIndex: 1,
        itemStyle: {
                normal: {
                color:'#F02FC2'},
        },
        data: lineData
    }, 
    {
        name: '笔记体积',
        type: 'bar',
        barWidth: 10,
        itemStyle: {
            normal: {
                barBorderRadius: 5,
                color: new echarts.graphic.LinearGradient(
                    0, 0, 0, 1,
                    [
                        {offset: 0, color: '#956FD4'},
                        {offset: 1, color: '#3EACE5'}
                    ]
                )
            }
        },
        data: barData
    }
   ]
};

app.plugins.plugins['obsidian-echarts'].render(options, this.container)

```

