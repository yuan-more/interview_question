# interview_question

## 第一题

### 1.1 解答
```python
num=0
with open('log.txt', 'r', encoding = 'utf-8') as f:
    for line in f:
        strArr=line.split('\t')
        if len(strArr)>10 and strArr[10].find('domain1.com')!=-1:
            num+=1         
print("第一题结果：",str(num))
```

### 1.2 解答
```python
import datetime

day_num=0
success_num=0
str_date='2019-02-28'
dt=datetime.datetime.strptime(str_date, '%Y-%m-%d').date()
with open('log.txt', 'r', encoding = 'utf-8') as f:
    for line in f:
        strArr=line.split('\t')
        try:
            if len(strArr)>3 and datetime.datetime.strptime(strArr[3], '[%d/%b/%Y:%H:%M:%S').date()==dt:
                day_num+=1
                if len(strArr)>8 and strArr[8]=='200':
                    success_num+=1
        except:
            pass
print(round(success_num/day_num,2))
```

## 第二题

### 解答
```sql
select
  count(*)
from (
  select 
    user_id 
  from event_log 
  where from_unixtime(event_timestamp,'yyyy-MM')='2020-09'
  group by user_id having count(user_id)>=1000 and count(user_id)<2000
) t
```

## 第三题

### 解答

![](https://qn.fivedata.cn/国际象棋比赛-数据模型[数据模型]-2022719113635.png)

DDL 语句：

```sql
DROP TABLE IF EXISTS players;
CREATE TABLE players(
    player_id VARCHAR(32) NOT NULL   COMMENT '棋手id' ,
    player_name VARCHAR(255)    COMMENT '棋手名称' ,
    club_id VARCHAR(32)    COMMENT '俱乐部id' ,
    rank INT    COMMENT '排名' ,
    join_date DATETIME    COMMENT '加入时间' ,
    quit_date DATETIME    COMMENT '更新时间' ,
    PRIMARY KEY (player_id)
)  COMMENT = '棋手表';

DROP TABLE IF EXISTS clubs;
CREATE TABLE clubs(
    club_id VARCHAR(32) NOT NULL   COMMENT '俱乐部id' ,
    club_name VARCHAR(255)    COMMENT '俱乐部名称' ,
    PRIMARY KEY (club_id)
)  COMMENT = '俱乐部表';

DROP TABLE IF EXISTS tournaments;
CREATE TABLE tournaments(
    tournament_id VARCHAR(32) NOT NULL   COMMENT '锦标赛id' ,
    tournament_name VARCHAR(255)    COMMENT '锦标赛名称' ,
    start_date DATETIME    COMMENT '开始日期' ,
    finish_date DATETIME    COMMENT '结束日期' ,
    club_id VARCHAR(32)    COMMENT '俱乐部id' ,
    PRIMARY KEY (tournament_id)
)  COMMENT = '锦标赛表';

DROP TABLE IF EXISTS matches;
CREATE TABLE matches(
    matches_id VARCHAR(32) NOT NULL   COMMENT '比赛id' ,
    matches_name VARCHAR(255)    COMMENT '比赛名称' ,
    player_id VARCHAR(32)    COMMENT '棋手id' ,
    is_winner INT    COMMENT '是否获胜' ,
    tournament_id VARCHAR(32)    COMMENT '锦标赛id' ,
    match_date DATETIME    COMMENT '比赛日期' ,
    match_session VARCHAR(32)    COMMENT '比赛场次' ,
    PRIMARY KEY (matches_id)
)  COMMENT = '比赛表';

DROP TABLE IF EXISTS sponsors;
CREATE TABLE sponsors(
    sponsor_id VARCHAR(32) NOT NULL   COMMENT '赞助商id' ,
    sponsor_name VARCHAR(255)    COMMENT '赞助商名称' ,
    tournament_id VARCHAR(32)    COMMENT '锦标赛id' ,
    PRIMARY KEY (sponsor_id)
)  COMMENT = '赞助商表';

```
