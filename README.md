**English** | [简体中文](README.zh-CN.md)

# Airbnb Search API

Search Airbnb listings by location and dates and get prices, ratings, coordinates and photos as JSON.

Powered by [Serpent API](https://apiserpent.com). Full reference: **[Airbnb Search API docs](https://apiserpent.com/airbnb-api)**.

## Quick start

1. Get an API key at [apiserpent.com](https://apiserpent.com). Every account starts with 10 free API calls.
2. Call the endpoint with your key in the `X-API-Key` header:

```bash
curl -G "https://apiserpent.com/api/airbnb/search" \
  --data-urlencode "location=Lisbon, Portugal" \
  --data-urlencode "adults=2" \
  -H "X-API-Key: $SERPENT_API_KEY"
```

## Endpoint

`GET https://apiserpent.com/api/airbnb/search`

| Parameter | Required | Description |
| --- | --- | --- |
| `location` | Yes | Place name in any language, e.g. `München`. Add a country when ambiguous. |
| `checkin` | No | `YYYY-MM-DD`. Send together with `checkout`. |
| `checkout` | No | `YYYY-MM-DD`. Send together with `checkin`. |
| `adults` | No | 1 to 16 |
| `room_type` | No | `any`, `entire_home`, `private_room` |
| `price_min` | No | Per night, US dollars |
| `price_max` | No | Per night, US dollars |

## Response

`success`, `location`, `checkin`, `checkout`, `listings[]` (up to 18). Each listing has `id`, `url`, `name`, `title`, `latitude`, `longitude`, `photo`, `badges[]`, `price_text`, `price`, `stay_nights`, `rating`, `reviews_count`.

See the [docs](https://apiserpent.com/airbnb-api) for the complete field list and sample responses.

## Examples

| File | Language | Run |
| --- | --- | --- |
| [`example.py`](example.py) | Python 3 (`pip install requests`) | `SERPENT_API_KEY=sk_live_... python example.py` |
| [`example.mjs`](example.mjs) | Node.js 18+ (no dependencies) | `SERPENT_API_KEY=sk_live_... node example.mjs` |

## Use cases

- Short-term rental market research
- Price monitoring across neighbourhoods
- Travel apps and trip planners

## More from Serpent API

- [Serpent API docs](https://apiserpent.com/docs) - Google, Bing, Yahoo, DuckDuckGo and Brave search, plus AI rank tracking
- [All SDKs and tools on GitHub](https://github.com/apiserpent)

## License

MIT
