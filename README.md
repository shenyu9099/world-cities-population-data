# 全球城市人口数据

本仓库用于城市人口规模分析，收录 Kaggle 的 **World cities database** 数据，并提供本项目使用的行政区归并版本。数据包含城市名称、经纬度、国家、行政区、首都类型和人口等信息，可用于人口分布、国家汇总、城市排名、首都类型结构和人口分箱分析。

## 数据来源

- Kaggle 数据集：[World cities database](https://www.kaggle.com/datasets/juanmah/world-cities)。
- Kaggle 发布者：[Juanma Hernández（juanmah）](https://www.kaggle.com/juanmah)。
- 网站注明的上游来源：[SimpleMaps World Cities Database](https://simplemaps.com/data/world-cities)。
- Kaggle 网站许可：[Creative Commons Attribution 4.0 International（CC BY 4.0）](https://creativecommons.org/licenses/by/4.0/)。
- 网站信息查阅与原始文件下载日期：2026年11月11日。

Kaggle 介绍指出，上游城市数据库整理了 NGIA、美国地质调查局、美国人口普查局及 NASA 等来源的数据，包含经纬度信息，以单个 CSV 文件提供城市记录，每条记录对应一座城市。网站介绍中的完整数据库超过440万条，基础版约5.02万条；本仓库实际收录的 CSV 为 **50,250 条记录、11个字段**，不是440万条的完整数据库。

本次从 Kaggle 下载的是第12版，网站显示该版本最后更新于2026年9月3日，介绍文字称数据于2026年8月30日刷新。**这些日期是网页和数据集的更新信息，不代表所有城市人口都统计于同一年。** CSV 未提供逐条人口统计年份。

## 数据文件

- [`worldcities.csv`](worldcities.csv)：本项目当前使用的版本，50,250条记录。已将香港、澳门、台湾相关记录归并到 `China / CN / CHN`，并补全对应行政区名称。
- [`upstream/kaggle-v12/worldcities.csv`](upstream/kaggle-v12/worldcities.csv)：2026年11月11日从 Kaggle 第12版下载的原始 CSV，逐字节保留，未进行行政区归并。
- [`upstream/project-original/worldcities.csv`](upstream/project-original/worldcities.csv)：本项目归并前的原始文件，用于追溯项目版本及190条记录的修改。该文件对应的 Kaggle 版本号尚未核实。
- [`metadata.json`](metadata.json)：各文件的记录数、字段、SHA256、网站介绍、版本及修改说明。

Kaggle 第12版原始文件的 `country` 有242个不同取值；项目归并版本有239个不同取值。这是当前文件中的类别数量，不作为全球国家数量的定义。

项目原始文件与本次下载的 Kaggle 第12版存在行政区等字段差异，因此项目版本不标注为第12版，也不将两个版本之间的全部差异归因于本次190条归并修改。

## 字段说明

- `city`：城市名称，可能含原文字符。
- `city_ascii`：城市名称的 ASCII 转写。
- `lat`：纬度，单位为度。
- `lng`：经度，单位为度。
- `country`：国家或地区名称，项目版本对指定记录进行了归并。
- `iso2`：两字母代码，项目版本相关记录统一为 `CN`。
- `iso3`：三字母代码，项目版本相关记录统一为 `CHN`。
- `admin_name`：行政区名称。
- `capital`：首都或行政首府类型；`primary` 为国家首都，`admin` 为一级行政区首府，`minor` 为二级行政区首府；空值表示未标注首府类型。
- `population`：原始文件中的人口数，单位为人，部分记录为空。
- `id`：城市记录标识，应按字符串读取。

## 项目版本的行政区修改

根据项目要求，对项目归并前文件中的190条记录进行了以下修改：

- 原 `iso2=HK` 的23条记录：`country=China`、`iso2=CN`、`iso3=CHN`、`admin_name=香港特别行政区`。
- 原 `iso2=MO` 的1条记录：`country=China`、`iso2=CN`、`iso3=CHN`、`admin_name=澳门特别行政区`。
- 原 `iso2=TW` 的166条记录：`country=China`、`iso2=CN`、`iso3=CHN`、`admin_name=台湾省`。

原有城市名称、人口、经纬度、首都类型和记录标识保持原值，记录顺序与总数保持不变。使用 `upstream/project-original/worldcities.csv` 可以核对修改前的原始行政区名称。

## 使用注意

CSV 使用 UTF-8 编码。两个来源版本及项目归并版本均有424条人口缺失记录、8条人口为零的记录。缺失不等于零，统计时应根据分析目标单独处理。

按国家求和仅表示文件内该国家城市记录的人口之和，不等于国家总人口或官方城镇人口。不同城市记录的人口统计边界和时间可能不同，应结合原始来源解释分析结果。

## 署名及许可

本仓库转载的数据来源于 Juanma Hernández 在 Kaggle 发布的 World cities database，Kaggle 页面注明数据源自 SimpleMaps，许可为 CC BY 4.0。请在使用或分发时保留来源、作者与许可链接，并说明所做修改。详细声明见 [LICENSE.md](LICENSE.md)。

可使用以下来源说明：

> Juanma Hernández. World cities database. Kaggle. https://www.kaggle.com/datasets/juanmah/world-cities . 上游来源：SimpleMaps World Cities Database. CC BY 4.0. 本仓库提供原始文件和行政区归并版本，修改内容见 README。
