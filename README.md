# 中国主要城市房价数据看板

这是一个可直接本地运行的房价数据看板示例，支持：

- 自动抓取国家统计局（70城）二手住宅价格指数数据。
- 按城市多选、时间区间筛选。
- 自动计算峰值、当前值、累计涨跌幅。
- 生成趋势图与汇总表格。

## 目录结构

- `dashboard.html`：主看板页面（仿示例样式）。
- `scripts/fetch_house_prices.py`：自动采集并清洗数据脚本。
- `data/house_price_index.json`：采集后的标准化数据文件。

## 快速开始

1. 抓取数据（联网）：

```bash
python3 scripts/fetch_house_prices.py
```

2. 启动本地静态服务：

```bash
python3 -m http.server 8000
```

3. 打开浏览器：

- <http://localhost:8000/dashboard.html>

## 数据来源说明

脚本优先尝试通过国家统计局数据接口自动获取数据；若接口临时不可用，可保留上一次抓取结果文件。

## 可扩展项

- 增加“新房价格指数”切换。
- 增加城市分组对比（核心城市群）。
- 通过 `cron` 或 GitHub Actions 定时执行抓取脚本，实现自动更新。
