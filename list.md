```
```
```dataviewjs
dv.list( dv.pages(``)
		.filter(p=>moment(Number(p.file.cday)).get("year")==2023)
		.sort(p=>p.file.cday,'desc')
		.map(p=>moment(Number(p.file.cday)).format('yyyy-MM-DD')+' >> '+p.file.link)
)
```
