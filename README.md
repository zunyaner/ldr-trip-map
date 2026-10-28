# 行程图（ldr-trip-map）

记录来回路径：地图上显示 from → to 连线，统计去了她的城市多少次。纯前端，数据存浏览器 localStorage。

## 打开

- 在线：https://zunyaner.github.io/ldr-trip-map/
- 本地：直接打开 `index.html`，或 `python3 -m http.server 8080`

> 地理编码在 `file://` 下可能受限，建议用本地 HTTP。

## 功能

- Leaflet + OpenStreetMap 地图图钉与路径
- 手动添加：日期、出发、到达、备注
- 设置「她的城市」→ 统计「去过她那里 × 次」（按 `to` 匹配）
- CSV / JSON 导入导出
- 行程列表、涉及城市

## 导入 CSV

列：`date,from,to,note`（也可用中文表头：日期,出发,到达,备注）

```csv
date,from,to,note
2024-05-01,上海,杭州,周末过去
2024-08-12,北京,杭州,
```

1. 下载「模板」或使用仓库内 `template.csv`
2. 填好后点「导入」
3. 等待地理编码，地图出现新路径

## License

MIT
