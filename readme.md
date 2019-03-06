# 知识数据库API

## 查询mention对应的实体entity

`http://172.16.13.52:5000/ment2ent?q=`

其中：
>参数q：要查询的mention

**实例：**

url：

`http://172.16.13.52:5000/ment2ent?q=王小波`

返回：

```
{"status": "Ok", "return": ["王小波（中国当代学者、作家）", "王小波（北宋农民起义领袖）", "王小波（遂宁市机保局副县级领导干部）", "王小波（湖南省永州市政协秘书长）", "王小波（浦北县开发投资集团有限公司董事长）", "王小波（广西自治区住房和城乡建设厅副巡视员）", "王小波（湖南省武冈市政协主席）", "王晓波（安徽农业大学农学院教师）"]}
```

返回值：
- status：返回状态
	- Ok:正常
	- None: 查询无结果
    - Error: url格式错误
- return：结果
	- mention所对应的所有entities


## 查询数据库中的三元组
`http://172.16.13.52:5000/triples?q=`

其中：
>参数q：要查询的entity

**实例：**

url：

`http://172.16.13.52:5000/triples?q=王小波（中国当代学者、作家）`

返回：

```
{"status": "Ok", "return": [["王小波（中国当代学者、作家）", "中文名", "王小波"], ["王小波（中国当代学者、作家）", "国籍", "中国"], ["王小波（中国当代学者、作家）", "民族", "汉"], ["王小波（中国当代学者、作家）", "出生地", "北京"], ["王小波（中国当代学者、作家）", "出生日期", "1952年05月13日"], ["王小波（中国当代学者、作家）", "逝世日期", "1997年04月11日"], ["王小波（中国当代学者、作家）", "职业", "学者、作家"], ["王小波（中国当代学者、作家）", "毕业院校", "美国匹兹堡大学东亚研究中心"], ["王小波（中国当代学者、作家）", "代表作品", "《黄金时代》、《白银时代》、《青铜时代》、《黑铁时代》、《沉默的大多数》"], ["王小波（中国当代学者、作家）", "DESC", "王小波（1952-1997），中国当代学者、作家。代表作品有《黄金时代》、《白银时代》、《青铜时代》、《黑铁时代》等。\n1952年5月13日，王小波出生于北京。他先后当过知青、民办教师、工人。1978年考入中国人民大学，1980年王小波与李银河结婚，同年发表处女作《地久天长》。1984年赴美匹兹堡大学东亚研究中心求学，2年后获得硕士学位。在美留学期间，游历了美国各地，并利用1986年暑假游历了西欧诸国。1988年回国，先后在北京大学，中国人民大学任教。1992年9月辞去教职，做自由撰稿人。他的唯一一部电影剧本《东宫西宫》获阿根廷国际电影节最佳编剧奖，并且入围1997年戛纳国际电影节。1997年4月11日病逝于北京，年仅45岁。"]]}
```

返回值：
- status：返回状态
- return：结果
   - 每个list是一个三元组

**注意**

此处的q应该是经过mention2entity查询后的，entity字符串。

例如：

`http://172.16.13.52/triples?q=王小波`

无结果
