# search-trends — 搜索与趋势（MCP 工具集）

谷歌搜索（Serper）+ Google Trends 多后端，共 **14 个只读工具**。

- 远程端点：`https://mcpweb.wjjnew.cn/search-trends/mcp`（Streamable HTTP）
- 鉴权：`Authorization: Bearer mcp_sk_xxx`（在 https://mcpweb.wjjnew.cn/ 注册获取）
- **平台内置上游密钥，远程托管无需自备 Key**
- 控制台 / 文档：https://mcpweb.wjjnew.cn/ · https://mcpweb.wjjnew.cn/search-trends-guide.html

## 客户端配置

```json
{
  "mcpServers": {
    "search-trends": {
      "type": "http",
      "url": "https://mcpweb.wjjnew.cn/search-trends/mcp",
      "headers": { "Authorization": "Bearer <你的 mcp_sk_xxx>" }
    }
  }
}
```

## 工具清单（14）

- **搜索（Serper，7）**：`web_search` `news_search` `image_search` `video_search` `scholar_search` `places_search` `autocomplete`
- **趋势（7）**：`trends_interest_over_time` `trends_growth` `trends_trending_now` `trends_interest_by_region` `trends_related_queries` `trends_related_topics` `trends_providers`

趋势工具可用 `provider`（`trendsmcp`/`hasdata`/`local`）覆盖默认后端；`trends_growth`/`trends_trending_now` 仅 `trendsmcp`。

## 计费

搜索 2 / 趋势(trendsmcp) 2 / 区域·相关词(hasdata) 5 / 趋势(local) 1（积分）；每用户每分钟调用上限。

## 本地部署（可选，自备密钥）

```bash
npm install && npm run build
node dist/index.js            # stdio
node dist/index.js --http --port=3000   # HTTP（默认监听 127.0.0.1）
```

环境变量见 `.env.example`：`SERPER_API_KEY`、`TRENDSMCP_API_KEY`、`HASDATA_API_KEY`、`DEFAULT_TRENDS_PROVIDER`。

## 许可

MIT（见 [LICENSE](./LICENSE)）。数据来自第三方公开接口，请遵守其条款。
