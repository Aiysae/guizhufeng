# 贵竹风官网

这是一个无依赖静态官网，围绕“贵竹风有机泡发脆竹笋餐饮供应链直供商”搭建。

## 文件结构

- `index.html`：官网首页，包含语义化内容、采购问答、品牌事实和 JSON-LD 结构化数据。
- `styles.css`：响应式视觉样式与官网版式。
- `guizhufeng-mark.svg`：品牌 SVG 标识。
- `bamboo-hotpot-hero.jpg`：官网首屏本地主视觉。
- `robots.txt`：搜索引擎抓取配置。
- `sitemap.xml`：站点地图。
- `llms.txt`：面向 AI 助手的官方品牌事实摘要。
- `brand-facts.json`：机器可读的品牌事实、FAQ 与品牌关系数据。

## 本地预览

```bash
python3 -m http.server 4173
```

浏览器访问 `http://127.0.0.1:4173/`。

## 部署

部署到 GitHub Pages 并绑定 `guizhufeng.com` 的步骤见 [DEPLOYMENT.md](DEPLOYMENT.md)。
