# 异地·足迹（LDR Trip Map）

异地恋行程 / 见面地图：在地图上标记城市图钉、按时间连线，支持 CSV/JSON 导入导出。纯前端，数据存浏览器 localStorage。

## 本地打开

直接用浏览器打开 `index.html`，或：

```bash
cd ldr-trip-map
python3 -m http.server 8080
# 访问 http://localhost:8080
```

> 地理编码（Nominatim）在部分浏览器对 `file://` 可能有 CORS 限制；若城市无法解析，请用本地 HTTP 服务打开。

## 功能

- Leaflet + OpenStreetMap 地图（无需 API Key）
- 手动添加：往返行程或单点见面，自动地理编码并缓存坐标
- CSV / JSON 导入与导出；可下载 CSV 模板
- 时间轴点击跳转图钉；统计见面次数、城市数、最近一次、下次倒数
- 首次为空时加载中国城市示例数据

## 如何导入 CSV

1. 点击页面「模板」下载 `ldr-trip-template.csv`，或使用仓库内 `template.csv`
2. 用 Excel / Numbers / 记事本编辑。**必填 `date`**（`YYYY-MM-DD`）
3. 行程填 `from` + `to`；单点见面填 `place`
4. 可选列：`title`, `note`, `tag`, `photo`
5. 点击「导入」选择文件 → 等待地理编码 → 地图出现新图钉

表头也支持中文：`日期,标题,出发,到达,地点,备注,标签,照片`

### CSV 示例

```csv
date,title,from,to,place,note,tag
2024-05-01,五一见面,北京,上海,,颐和园散步后高铁,见面
2024-10-01,国庆旅行,,,丽江,古城慢行,旅行
```

### JSON 示例

```json
{
  "version": 1,
  "trips": [
    {
      "date": "2024-05-01",
      "title": "五一见面",
      "from": "北京",
      "to": "上海",
      "note": "颐和园散步后高铁",
      "tag": "见面"
    }
  ]
}
```

## 技术说明

- 地图：Leaflet + OSM tiles
- 地理编码：Nominatim（约 1 请求/秒，坐标缓存于 localStorage）
- 无账号、无后端、无付费地图

## License

MIT — 随意给你们两个人用 ♡
