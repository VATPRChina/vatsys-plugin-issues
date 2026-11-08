# Data 数据说明

本目录存放 vatSys-VATPRC-Plugin 和扇区导出使用的数据。

## 文件列表

| 文件或目录 | 用途 |
| --- | --- |
| [Airports/](Airports/) | 机场箭头和关闭区域地图数据。填写方式见 [Airports 说明](Airports/README.md)。 |
| [Clearance.txt](Clearance.txt) | 机场放行辅助数据，包括机场标高、初始爬升高度和机型限制。 |
| [Sid.txt](Sid.txt) | 离场程序数据，按机场、出口点和跑道等条件填写。 |
| [Wingspan.txt](Wingspan.txt) | 机型翼展数据，用于机场接收能力检查和机位分配。 |
| [Datis.json](Datis.json) | D-ATIS 机场信息、频率和预设。 |
| [XFL.json](XFL.json) | 移交点及可用移交高度规则。 |
| [ICAO_Airlines.txt](ICAO_Airlines.txt) | 航空公司代码、名称和呼号数据。 |
| [ICAO_Airports.txt](ICAO_Airports.txt) | 机场代码和名称数据。 |

## ICAO 数据

**请不要手动修改 `ICAO_Airlines.txt` 和 `ICAO_Airports.txt`。** 这两个文件会不定期覆盖更新，手动修改的内容会被覆盖。

维护其他文件时，请保留现有字段、编码和数据格式。机场地图数据的图层及坐标格式见 [Airports 说明](Airports/README.md)。
