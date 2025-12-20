# 南山经 - 鹊山山系

- [南山经 - 鹊山山系](#南山经---鹊山山系)
  - [鹊山山系的山](#鹊山山系的山)
  - [文言文](#文言文)
  - [白话文](#白话文)
  - [建模](#建模)

## 鹊山山系的山

- [其首曰招瑶之山](./nanshanjing01/nanshanjing01-01.md)
- [又东三百里曰堂庭之山]()
- [又东三百八十里曰猨翼之山]()
- [又东三百七十里曰杻陽之山]()
- [又东三百里柢山]()
- [又东三百里曰亶爰之山]()
- [又东三百曰基山]()
- [又东三百里曰青丘之山]()
- [又东三百五十里曰箕尾之山]()

## 文言文

```
凡鹊山之首，自招摇之山以至箕尾之山，凡十山，二千九百五十里，其神状皆鸟身而龙首。其祠之礼：毛，用一璋玉瘗；糈用稌米，一壁，稻米、白莹为席。
```

## 白话文

```
总计鹊山山系之首尾，从招摇山起，直到箕尾山止，一共是十座山，途经二千九百五十里。诸山山神的形状都是鸟的身子龙的头。祭祀山神的典礼；是把畜禽和璋一起埋入地下，祀神的米用稻米，用白茅草来做神的座席。
```

## 建模

```cypher
MATCH (j:Jing {name:"南山经第一"})
MERGE (sl:MountainList:山系 {id:"nanshanjing01", name:"鹊山"})
MERGE (s01:Mountain:山 {id:"nanshanjing01-01", name:"招瑶之山"})
MERGE (s02:Mountain:山 {id:"nanshanjing01-02", name:"堂庭之山"})
MERGE (s03:Mountain:山 {id:"nanshanjing01-03", name:"猨翼之山"})
MERGE (s04:Mountain:山 {id:"nanshanjing01-04", name:"杻陽之山"})
MERGE (s05:Mountain:山 {id:"nanshanjing01-05", name:"柢山"})
MERGE (s06:Mountain:山 {id:"nanshanjing01-06", name:"亶爰之山"})
MERGE (s07:Mountain:山 {id:"nanshanjing01-07", name:"基山"})
MERGE (s08:Mountain:山 {id:"nanshanjing01-08", name:"基山"})
MERGE (s09:Mountain:山 {id:"nanshanjing01-09", name:"箕尾之山"})
MERGE (j)-[r1:包括]->(sl)-[r2:包括]->(s01)
MERGE (s01)-[r01:NEXT_TO]->(s02)-[r02:NEXT_TO]->(s03)-[r03:NEXT_TO]->(s04)-[r04:NEXT_TO]->(s05)-[r05:NEXT_TO]->(s06)-[r06:NEXT_TO]->(s07)-[r07:NEXT_TO]->(s08)-[r08:NEXT_TO]->(s09)
SET
    r01.direction = "向东", r01.distance = 300, r01.distanceUnit = "里",
    r02.direction = "向东", r02.distance = 380, r02.distanceUnit = "里",
    r03.direction = "向东", r03.distance = 370, r03.distanceUnit = "里",
    r04.direction = "向东", r04.distance = 300, r04.distanceUnit = "里",
    r05.direction = "向东", r05.distance = 300, r05.distanceUnit = "里",
    r06.direction = "向东", r06.distance = 300, r06.distanceUnit = "里",
    r07.direction = "向东", r07.distance = 300, r07.distanceUnit = "里",
    r08.direction = "向东", r08.distance = 350, r08.distanceUnit = "里"
RETURN j, sl, s01, s02, s03, s04, s05, s06, s07, s08, s09, r1, r2, r01, r02, r03, r04, r05, r06, r07, r08
```

创建`鹊山山系`各个山脉与山系关系如下：

![nanshanjing01-mountains](img/nanshanjing01-mountains.png)