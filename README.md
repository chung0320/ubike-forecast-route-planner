# MDS
解決問題：尖峰時段司機補車效率不及需求量，所以提出最佳化路徑

## 分工
- 處理預測:
- OR:
- 模擬補車結果+比較:Jasmine


## Overview
* 資料集(即時資料：6個月/3個月/1個月） 
* 預處理
    * 時間切割
    * 是否假日
    * 選擇站點
* 預測 LSTM 去預測結果 overfitting
* 尖峰時候的路徑規劃： google or tool 跑結果 或 比較演算法的效率 

## 假設
- 司機從公館捷運站 3 號出口開始出發
- 缺車率小於 30% 司機會去補車；大於 70% 會去拉車
- 每個站點維持 50% 的空車率
- 補一台車需要 30 秒（從車上把車放下來放到）
- 大站點拉 25 台車（大的站點）

## Prediction

### Schema
- independent variable: {待捕}
- dependent variable: 站點缺車率

### preprocessing
- 預期目標:哪些方法？是什麼資料特性要這樣使用？
- 9 10 11 預測 12，並剔除放假的特定節日
- 平日
- 預測公館站

### model *2
- 預期目標:解釋哪一些變數對於預測比較重要


## OR *2
- 預期目標：
    - 演算法去預測路徑規劃
    - 模擬補車結果
    - 比較歷史資料(目前司機的解決方法：去檢查水位、一天四次)與模擬的結果
    - 列出優點(時間、油量、近需求)
- 備料：
    - 選台大校園的站:台大外圍站點+內部
    - 使用 Google Map API 取得站點位置
    - 參數：
        - 經緯度 轉 distance
        - num_of_bike(缺車率＊總車數) 
        - 3台貨車：兩大（24輛）一小（16輛）
    - 考量因素：
        - 缺車率
        - 熱門程度
        - 使用率
- 演算法
    - Greedy(挑最近的)
    - Genetic 
    - Simulated Annealing


### References
- [Google OR Tools](https://developers.google.com/optimization/install?hl=zh-tw)
- [OR Tools 解車輛路徑問題](https://developers.google.com/optimization/routing/vrptw?hl=zh-tw)
- [最佳化理論](https://medium.com/jimmy-wang/%E6%9C%80%E4%BD%B3%E5%8C%96%E7%90%86%E8%AB%96-optimization-theory-406d02c5a411)
- [啟發式演算法](https://www.baeldung.com/cs/greedy-vs-heuristic-algorithm)
- [Greedy Algorithm](https://medium.com/ivymobility-developers/algorithm-a168afcd3611)
- [Genetic Algorithm](https://ithelp.ithome.com.tw/articles/10211706?sc=pt)
- [Simulated Annealing](https://cloud.tencent.com/developer/article/1424760)
- [時間與空間複雜度](https://hackmd.io/@joe94113/time_complexity_and_space_complexity)
- [車輛路徑問題（VRP, Vehicle Routing Problem)](https://www.youtube.com/watch?v=OKMssWdC0I0)
- [旅行銷售員問題（TSP, Travelling Salesman Problem](https://www.youtube.com/watch?v=1pmBjIZ20pE)
- [容量限制的車輛路徑問題（CVRP, Capacitated Vehicle Routing Problem)](https://developers.google.com/optimization/routing/cvrp?hl=zh-tw)
- [時間窗限制的車輛路徑問值（VRPTW, Vehicle Routing Problem with Time Windows）](https://developers.google.com/optimization/routing/vrptw?hl=zh-tw)