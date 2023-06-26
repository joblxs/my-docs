---
banner: "https://api.dujin.org/bing/1920.php"
cssclass: fullwidth,noyaml,noscroll,myhome
obsidianUIMode: preview
---

```ad-icon
<svg xmlns="http://www.w3.org/2000/svg" aria-label="Calendar" role="img" viewBox="0 0 512 512">
  <path d="M512 455c0 32-25 57-57 57H57c-32 0-57-25-57-57V128c0-31 25-57 57-57h398c32 0 57 26 57 57z" fill="#e0e7ec"></path>
  <path d="M484 0h-47c2 4 4 9 4 14a28 28 0 1 1-53-14H124c3 4 4 9 4 14A28 28 0 1 1 75 0H28C13 0 0 13 0 28v157h512V28c0-15-13-28-28-28z" fill="#cf5659"></path>
 <g fill="#f3aab9">
        <circle cx="462" cy="136" r="14"/>
        <circle cx="462" cy="94" r="14"/>
        <circle cx="419" cy="136" r="14"/>
        <circle cx="419" cy="94" r="14"/>
        <circle cx="376" cy="136" r="14"/>
        <circle cx="376" cy="94" r="14"/>
      </g>
  <text id="month" x="32" y="164" fill="#fff" font-family="-apple-system, BlinkMacSystemFont, 'Noto Sans', 'Noto Sans CJK SC', 'Microsoft YaHei', 微软雅黑, sans-serif, 'Segoe UI', Roboto, 'Helvetica Neue', Arial" font-size="122px" style="text-anchor: left"><%+ tp.date.now("MMMM").toUpperCase() %>
  </text>
  <text id="day" x="256" y="400" fill="#333" font-family="-apple-system, BlinkMacSystemFont, 'Noto Sans', 'Noto Sans CJK SC', 'Microsoft YaHei', 微软雅黑, sans-serif, 'Segoe UI', Roboto, 'Helvetica Neue', Arial" font-size="256px" style="text-anchor: middle"><%+ tp.date.now("D") %>
  </text>
  <text id="weekday" x="256" y="480" fill="#66757f" font-family="-apple-system, BlinkMacSystemFont, 'Noto Sans', 'Noto Sans CJK SC', 'Microsoft YaHei', 微软雅黑, sans-serif, 'Segoe UI', Roboto, 'Helvetica Neue', Arial" font-size="64px" style="text-anchor: middle"><%+ tp.date.now("dddd") %>
  </text>
</svg>

```

%%问候和天气数据 %%
%% 动画猫 %%
```jsx::AnimationCat
```
%% --文字版天气加图标--开始 %%

>[!note|noborder banner]  &nbsp;
>```dataviewjs
let setting = {};
let history = Object.assign(JSON.parse(await app.vault.adapter.read(".obsidian/.diary-stats")));
let today = moment().format("YYYY-MM-DD");
let moonIndex = moment().diff(moment().startOf('year'),"hours").toString().padStart(4, '0')
if (history.hasOwnProperty(today))
{let weather=history[today].weather;
let todayweather = weather[0];
setting.iconDay =  weather[0].iconDay;
setting.windSpeedDay =  weather[0].windSpeedDay;
setting.windSpeedNight =  weather[0].windSpeedNight;
await dv.view("dv_weatherSvg",setting)
let desc = ` <%+ tp.date.now("A好，今天是YYYY年MM月Do dddd") %> ，${todayweather.city} ${todayweather.textDay}， ${todayweather.tempMin}~${todayweather.tempMax}℃  ${todayweather.air} ${todayweather.windydesc} [[最近天气查询|✈️]] 云朵充盈了${todayweather.cloud}%的天空\n顺便，月亮会在${todayweather.moonrise} 时浮起，${todayweather.moonset} 时沉落\n 如果足够幸运碰见它的话，我想它应该是这样的👉🏻`;
dv.paragraph(desc + `<img style="margin-top:-50px;vertical-align: bottom; -webkit-clip-path: circle(42.55% at 50% 50%);" width="50" alt="|inl" src="https://svs.gsfc.nasa.gov/vis/a000000/a004900/a004955/frames/216x216_1x1_30p/moon.${moonIndex}.jpg">`);
}
>```

%% ---文字版天气加图标--结束 %%

---

````ad-flex
> [!profile-card|cards]  `button-refreshhomepage1`
> ***快乐摸鱼又一天***
> %%**瞅瞅你的笔记写了多少篇**%%
>>[!profile-card-inf|noborder]
>>```dataviewjs
>>let nofold = '!"static"'
>>let ftMd = dv.pages("").file.sort(t => t.cday)[0]
>>let total = parseInt([new Date() - ftMd.ctime] / (60*60*24*1000))
>>let allFile = dv.pages(nofold).file
>>dv.paragraph(`
>>>[!item|noborder] [[echarts-笔记动态显示-分布|${total}]]
>>> Ob天数
>>
>>>[!item|noborder] [${allFile.length}](obsidian://advanced-uri?commandid=obsidian-better-command-palette%253Aopen-better-commmand-palette-file-search)
>>> 文档
>>
>>>[!item|noborder] [[文件夹所有标签|${allFile.etags.distinct().length}]]
>>> 标签
>>
>>>[!item|noborder] [[任务卡片-dataview 任务查询举例#所有未完成的任务|${allFile.tasks.length}]]
>>> 事项`)
>>```

%%notice1%%
> [!stickies3]
> #### 倒计时
>> 今年已过去 <%+* tR+= moment().diff(tp.date.now("YYYY-1-1"), "days") %> 天
>> 
>> 距春节还有<%+* let edate = moment("2022-02-01", "yyyy-MM-DD"); let from = moment().startOf('day'); edate.diff(from, "days") >= 0 ? tR += edate.diff(from, "days") : tR += edate.add(1, "year").diff(from, "days") %> 天

%%notice2%%
> [!stickies3|pink]
> #### 每日一句
> ```dataviewjs
 let history = Object.assign(JSON.parse(await app.vault.adapter.read(".obsidian/.diary-stats")));
 let today = moment().format("YYYY-MM-DD");
 if (history.hasOwnProperty(today))
 {
 let quotes=history[today].quotes;
 dv.paragraph(quotes);
 }
> ```

%%notice3%%
> [!stickies3|green]
> ### 💌
> 开启美好的一天

````
