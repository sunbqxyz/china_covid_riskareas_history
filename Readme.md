# 风险区域历史数据集

## 数据描述

为2020年7月29日至2022年4月15日，共625天中国新型冠状病毒风险区域的记录。

## 数据来源

从贵州及浙江卫健委相关通告中获取，原始文本文件参考[Raw_data](Raw_data)，通过数据清洗整理为json格式。

其中，200925、201004、210720、210809、211004、211025、211026、211027共8天的数据缺失，通过手工录入。

此外，210723-211023数据来自贵州省卫健委，其余数据来源于浙江省卫健委。

## 数据格式

List(Dict)

Dict({'end_update_time', 'hcount', 'mcount', 'lcount', 'highlist', 'middlelist', 'lowlist'})

count 分别为风险区计数，与list长度一致

list为地区列表，长度为4,分别代表[省，市，县，详细地址]，通过[CPCA](https://github.com/DQinYuan/chinese_province_city_area_mapper)机器分割，部分地址县级为None。

## 提醒

- 2022年4月15日后数据可以通过[RiskLevelAPI](https://github.com/panghaibin/RiskLevelAPI/tree/api)获取
- 官方的风险地区分级最早开始于2月21日新型冠状病毒肺炎防控方案（第五版）相关要求，但早期互联网相关信息缺乏，从5月10左右可通过搜索引擎查找到“《国务院客户端》国内疫情风险等级情况”相关的风险地区情况，但时间不连续，故暂未收集

## Update

history_mod.json 中补足了56个地点的地市名缺失，目前所有地点的省、市两级名称均存在。

