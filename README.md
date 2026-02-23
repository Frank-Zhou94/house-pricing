# 中国主要城市房价数据看板

这是一个可直接本地运行的房价数据看板示例，支持：

- 自动抓取/加载房价指数数据（多源尝试）。
- 按城市多选、时间区间筛选（起止后曲线按区间截断展示）。
- 自动计算峰值、当前值、累计涨跌幅、跌回时间。
- 生成趋势图、汇总表格，并绘制“跌回 20xx-xx”参考线。

## 目录结构

- `dashboard.html`：主看板页面（仿示例样式）。
- `scripts/fetch_house_prices.py`：自动采集并清洗数据脚本。
- `data/house_price_index.json`：采集后的标准化数据文件。

## 快速开始

1. 抓取数据：

```bash
python3 scripts/fetch_house_prices.py
```

2. 启动本地静态服务：

```bash
python3 -m http.server 8000
```

3. 打开浏览器：

- <http://localhost:8000/dashboard.html>

## 数据源策略（自动）

脚本按如下顺序尝试：

1. 国家统计局接口。
2. 自定义 JSON 远程地址（可选）：环境变量 `HOUSE_PRICE_JSON_URL`。
3. 本地镜像文件（可选）：`data/house_price_index_mirror.json`。
4. 若都失败，回退到演示序列，保证看板可用。

## 当前城市

北京、上海、广州、深圳、杭州、南京、武汉、成都、西安、天津、无锡、苏州、厦门。
