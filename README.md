![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Find All Collation Across All Columns With SQL
**Post Date: April 8, 2015**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Find the column collation across all tables with this piece of SQL logic.
Do you have this error? Implicit conversion of varchar value to varchar cannot be performed because the collation of the value is unresolved due to a collation conflict between "Latin1_General_CI_AS" and "SQL_Latin1_General_CP1_CI_AS" in add operator. [SQLSTATE 42000] (Error 457).
You may find a collation issue with some of your queries particularly whenever joins are involved. You can solve this problem by simply adjusting your query to include the suffice COLLATION 'MyServerCollation', but this will of course only affect that current query. The question remains; how many other columns have different collations across how many tables? What are those columns anyway?
Use this SQL logic to get that answer.</p>

---
## SQL-Logic
```SQL
select
'table name' = object_name(sc.id)
,   'column' = sc.name
,   'collation' = sc.collation
from
syscolumns sc
where
objectproperty([id], 'isusertable')=1
and collation is not null
--and   collation &lt;&gt; 'sql_latin1_general_cp1_ci_as'
order by
object_name(sc.id), sc.name asc
```

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- [![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
- [![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
- [![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)


---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

