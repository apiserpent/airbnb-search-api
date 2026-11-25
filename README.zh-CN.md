[English](README.md) | **简体中文**

# Airbnb 房源搜索 API

按地点和日期搜索 Airbnb 房源，以 JSON 返回价格、评分、经纬度和照片。

由 [Serpent API](https://apiserpent.com) 提供。完整文档：**[Airbnb Search API 文档](https://apiserpent.com/airbnb-api)**。

## 快速开始

1. 在 [apiserpent.com](https://apiserpent.com) 注册并获取 API Key，每个账号赠送 10 次免费调用。
2. 在请求头 `X-API-Key` 中带上你的 Key 调用接口：

```bash
curl -G "https://apiserpent.com/api/airbnb/search" \
  --data-urlencode "location=Lisbon, Portugal" \
  --data-urlencode "adults=2" \
  -H "X-API-Key: $SERPENT_API_KEY"
```

## 接口

`GET https://apiserpent.com/api/airbnb/search`

| 参数 | 必填 | 说明 |
| --- | --- | --- |
| `location` | 是 | 地点名称，支持任意语言，例如 `München`；有歧义时请加上国家。 |
| `checkin` | 否 | 入住日期，格式 `YYYY-MM-DD`，需与 `checkout` 同时传入。 |
| `checkout` | 否 | 退房日期，格式 `YYYY-MM-DD`，需与 `checkin` 同时传入。 |
| `adults` | 否 | 成人数量，1 到 16 |
| `room_type` | 否 | `any`、`entire_home`、`private_room` |
| `price_min` | 否 | 每晚最低价（美元） |
| `price_max` | 否 | 每晚最高价（美元） |

## 返回结果

顶层字段：`success`、`location`、`checkin`、`checkout`、`listings[]`（最多 18 条）。每条房源包含 `id`、`url`、`name`、`title`、`latitude`、`longitude`、`photo`、`badges[]`、`price_text`、`price`、`stay_nights`、`rating`、`reviews_count`。

完整字段列表和响应示例请参阅[文档](https://apiserpent.com/airbnb-api)。

## 示例代码

| 文件 | 语言 | 运行方式 |
| --- | --- | --- |
| [`example.py`](example.py) | Python 3（`pip install requests`） | `SERPENT_API_KEY=sk_live_... python example.py` |
| [`example.mjs`](example.mjs) | Node.js 18+（无需依赖） | `SERPENT_API_KEY=sk_live_... node example.mjs` |

## 应用场景

- 短租市场调研
- 不同区域的价格监控
- 旅行应用与行程规划工具

## Serpent API 的更多能力

- [Serpent API 文档](https://apiserpent.com/docs)：Google、Bing、Yahoo、DuckDuckGo 和 Brave 搜索结果，以及 AI 引用排名跟踪
- [GitHub 上的全部 SDK 与工具](https://github.com/apiserpent)

## 许可证

MIT
