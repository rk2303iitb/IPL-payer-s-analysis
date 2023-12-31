# Introduction


I have always had a profound love for cricket, driven in part by its rich tapestry of data and statistics. While the ICC provides ranking systems, I found them confusing and opaque. Moreover, there seemed to be a lack of a data-based method to comprehensively rank players based on their cumulative performance.

In my quest for a more transparent and insightful approach, I stumbled upon the [Run Above Average](http://www.cricmetric.com/blog/2012/02/a-context-independent-method-of-ranking-odi-players/) method for ranking batters. Intrigued, I decided to apply this methodology to IPL data, aiming to provide a fresh perspective on player rankings.

SO basially, I've tried to extract following(and potentially other rankings when I'll get some time XD)-
   1. Ranking based on Run above average- [SQL code](https://github.com/rk2303iitb/IPL-payers-analysis/blob/main/Run%20above%20average%20query.md#query-for-run-above-average)
   2. Ranking based on maiden overs- [SQL code](https://github.com/rk2303iitb/IPL-payers-analysis/blob/main/Maiden%20overs%20query.md#sql-query-for-maiden-overs)

Dataset used- [Indian Premier league(IPL Cricket) till 2016 - dataset by raghu543](https://data.world/raghu543/ipl-data-till-2016-set-of-csv-files)
- Publically available database with ball by ball records till IPL 2016
- Total 21 different tables present in the data base
- Used 4 tables(ball_by_ball, batsman_scored, wicket_taken, player) for Run above average case study
- Used 4 tables(ball_by_ball, batsman_scored, extra_runs, player) for maiden over case study

## Results
- Run above average(excluding batters with zero outs)
[runs-above-average.csv](https://github.com/rk2303iitb/IPL-payers-analysis/files/13800615/runs-above-average.csv)

![Screenshot 2023-12-31 135927](https://github.com/rk2303iitb/IPL-payers-analysis/assets/155146605/26d5cff4-aef2-4be5-81d3-66873a79ecae)
  
- Maiden overs
[maiden-bowlers.csv](https://github.com/rk2303iitb/IPL-payers-analysis/files/13800619/maiden-bowlers.csv)

![Screenshot 2023-12-31 140054](https://github.com/rk2303iitb/IPL-payers-analysis/assets/155146605/7094bbc9-c2d8-428b-b9ad-566920eb2ef1)

