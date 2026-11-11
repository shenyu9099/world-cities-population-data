# World cities database

Accurate and up-to-date database of the world's cities and towns

## About Dataset

The data is from:

https://simplemaps.com/data/world-cities

We're proud to offer a simple, accurate and up-to-date database of the world's cities and towns. We've built it from the ground up using authoritative sources such as the NGIA, US Geological Survey, US Census Bureau, and NASA.
   
Our database is:

- Up-to-date: It was last refreshed on August 30, 2026.
- Comprehensive: Over 4.4 million unique cities and towns from every country in the world (about 50.2 thousand in basic database).
- Accurate: Cleaned and aggregated from official sources. Includes latitude and longitude coordinates.
- Simple: A single CSV file, concise field names, only one entry per city.

## 字段说明

- `city`：城市名称，保留原文字符和重音符号。
- `city_ascii`：城市名称的 ASCII 转写形式。
- `lat`：纬度，单位为十进制度；北纬为正，南纬为负。
- `lng`：经度，单位为十进制度；东经为正，西经为负。
- `country`：国家或地区名称。
- `iso2`：两位字母国家或地区代码，例如中国为 `CN`。
- `iso3`：三位字母国家或地区代码，例如中国为 `CHN`。
- `admin_name`：城市所属行政区名称。
- `capital`：首都或行政首府类型；`primary` 表示国家首都，`admin` 表示一级行政区首府，`minor` 表示下级行政区首府；空值表示未标注首府类型。
- `population`：人口数量，单位为人；空值表示未提供人口数据。
- `id`：城市记录标识，建议按文本读取。

## License

[Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)

[Juanma Hernández](https://www.kaggle.com/juanmah) · [Kaggle](https://www.kaggle.com/datasets/juanmah/world-cities)
