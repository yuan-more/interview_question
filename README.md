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
