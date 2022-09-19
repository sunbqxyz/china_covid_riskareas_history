# 风险区域历史数据集

## 数据描述

为2020年7月29日至2022年4月15日，共625天中国新型冠状病毒风险区域的记录，共包含4k个风险地区的35k条记录。

当前最新版本为[history_mod2.json](/history-mod2.json)

## 数据来源

从贵州及浙江卫健委相关通告中获取，原始文本文件参考[Raw_data](Raw_data)，通过数据清洗整理为json格式。

其中，200925、201004、210720、210809、211004、211025、211026、211027共8天的数据缺失，通过手工录入。

此外，210723-211023数据来自贵州省卫健委，其余数据来源于江苏省卫健委。

由于提取过程导致的2390个位置的部分地理信息缺失，通过高德地图地址编码API补足了其中的2310个地区，剩余地区通过手工补录完成。手工补录的前后对比参见[fixed.json](Raw_data/fixed.json)，完整对比参见[fixed_byhand.json](Raw_data/fixed.json)

## 数据格式

List(Dict)

Dict({'end_update_time', 'hcount', 'mcount', 'hlist', 'mlist'})

count 分别为风险区计数，与list长度一致

list为地区列表，长度为4,分别代表[省，市，县，详细地址]，通过[CPCA](https://github.com/DQinYuan/chinese_province_city_area_mapper)机器分割，部分县级地址通过高德地图API补足，同时部分地址最低级为空字符串，表示风险区域为全域。

## 提醒

- 2022年4月15日后数据可以通过[RiskLevelAPI](https://github.com/panghaibin/RiskLevelAPI/tree/api)获取；
- 官方的风险地区分级最早开始于2月21日新型冠状病毒肺炎防控方案（第五版）相关要求，但早期互联网相关信息缺乏，从5月10左右可通过搜索引擎查找到“《国务院客户端》国内疫情风险等级情况”相关的风险地区情况，但时间不连续，故暂未收集；
- 由于数据在一天内可能多次进行更新，同时卫健委大部分网页未写明更新时间，故部分数据可能和您获取的同日期数据存在部分差异。
- [Jiangsu](Raw_Data/Jiangsu)文件夹下的文件名中的日期可能对应2020/2021/2022年，对于这一问题，可以先按照文件名将其分割为标题以日期开头和以“截止”开头的两类，其中“截止”开头的对应较靠后的日期。

## Update

history_mod.json 中补足了56个地点的地市名缺失，目前所有地点的省、市、县两级名称均存在。

根据 [Issue 1](https://github.com/sunbqxyz/china_covid_riskareas_history/issues/1)修正了文件命名和原始文本缺失的问题

https://github.com/sunbqxyz/china_covid_riskareas_history/issues/1)

## 已知存在的问题

- 采用的卫健委信源并非完全准确，如原文本210808中“武汉市龙示范区学林街道（新增）”在其他互联网版本中不存在
- 数据验证仅保证了分割得到的风险区数量与文本中提到的风险区数量一致，可能存在同时一分为二和合二为一的数据

