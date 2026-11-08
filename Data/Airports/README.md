# 机场箭头和关闭区域数据

本目录按机场 ICAO 代码存放地面地图数据。`XXXX_Arrow.json` 用于箭头、线条和文字，`XXXX_Close.json` 用于关闭区域。

```text
Airports/
└── ZGGG/
    ├── ZGGG_Arrow.json
    └── ZGGG_Close.json
```

文件名、文件夹名和 JSON 中的 `airport` 使用相同的四位机场 ICAO 代码。没有箭头或关闭区域时，不需要创建对应文件。例如，只有关闭区域的机场只需提供 `XXXX_Close.json`。

## 图层

每个对象代表一个图层，`geometry` 中的每一项代表一个图形。同一图层的图形放在同一个 `geometry` 数组中。

- 不填写 `layer`：生成默认 Map，例如 `ASMGCS_ZGGG_Arrow` 或 `ASMGCS_ZGGG_Closed`。
- 填写 `"layer": "North"`：生成 `ASMGCS_ZGGG_Arrow(North)` 或 `ASMGCS_ZGGG_Closed(North)`。
- `layer` 的内容就是 Map 名称括号中的文字，例如 `North`、`South`、`East`、`West`；可以按实际用途命名。

图层名称不控制跑道启用状态。在 vatSys 的 Map 列表中选择需要显示的图层。

## 坐标

坐标使用十进制度，顺序为 **[纬度, 经度]**。北纬、东经为正；南纬、西经为负。

```json
[23.398756, 113.281885]
```

多边形按边界顺序填写坐标，至少需要三个点。首尾不相同时，导出程序会自动闭合。线条至少需要两个点。每个独立多边形单独写成一项。

以下坐标仅用于说明格式，不代表实际机场图形。

## Arrow 文件

`arrows` 是图层列表。每个图层的 `geometry` 支持：

- `polygon`：多边形，用 `coordinates` 填写各顶点。
- `line`：线条，用 `coordinates` 填写线上的点。
- `text`：文字，用 `text` 填写内容，用 `position` 填写位置。

```json
{
    "airport": "ZGGG",
    "arrows": [{
            "geometry": [{
                    "type": "polygon",
                    "coordinates": [[23.4, 113.2], [23.41, 113.2], [23.4, 113.21]]
                }]
        }, {
            "layer": "North",
            "geometry": [{
                    "type": "line",
                    "coordinates": [[23.4, 113.2], [23.41, 113.21]]
                }, {
                    "type": "text",
                    "text": "A",
                    "position": [23.4, 113.2]
                }]
        }]
}
```

## Close 文件

`closed_areas` 是图层列表。关闭区域使用 `polygon`，多个独立区域分别写在 `geometry` 数组中。

```json
{
    "airport": "ZGGG",
    "closed_areas": [{
            "geometry": [{
                    "type": "polygon",
                    "coordinates": [[23.4, 113.2], [23.41, 113.2], [23.4, 113.21]]
                }, {
                    "type": "polygon",
                    "coordinates": [[23.42, 113.2], [23.43, 113.2], [23.42, 113.21]]
                }]
        }, {
            "layer": "North",
            "geometry": [{
                    "type": "polygon",
                    "coordinates": [[23.44, 113.2], [23.45, 113.2], [23.44, 113.21]]
                }]
        }]
}
```
