# 贵竹风官网部署计划

目标：把当前静态官网部署到 GitHub Pages，并绑定腾讯云已购买域名 `guizhufeng.com`。

## 1. GitHub 仓库准备

建议仓库名：

```bash
guizhufeng-official-site
```

仓库建议设置：

- Visibility：Public（GitHub Free 使用 GitHub Pages 最稳）
- 默认分支：`main`
- 部署方式：GitHub Pages / Deploy from a branch
- 发布目录：`main` 分支的 `/root`

## 2. 本地代码推送

如果 GitHub 上已创建空仓库，复制仓库地址后执行：

```bash
git remote add origin git@github.com:<your-account>/guizhufeng-official-site.git
git push -u origin main
```

如果使用 HTTPS：

```bash
git remote add origin https://github.com/<your-account>/guizhufeng-official-site.git
git push -u origin main
```

## 3. GitHub Pages 设置

进入 GitHub 仓库：

```text
Settings -> Pages
```

配置：

- Source：Deploy from a branch
- Branch：`main`
- Folder：`/root`
- Custom domain：`guizhufeng.com`
- 勾选：Enforce HTTPS

说明：仓库根目录已经包含 `CNAME` 文件，内容为 `guizhufeng.com`。GitHub Pages 会用它识别自定义域名。

## 4. 腾讯云 DNS 解析

在腾讯云域名控制台进入 `guizhufeng.com` 的 DNS 解析，添加以下记录。

### 根域名 guizhufeng.com

添加 4 条 A 记录：

| 主机记录 | 记录类型 | 记录值 |
| --- | --- | --- |
| @ | A | 185.199.108.153 |
| @ | A | 185.199.109.153 |
| @ | A | 185.199.110.153 |
| @ | A | 185.199.111.153 |

### www 子域名

添加 1 条 CNAME 记录：

| 主机记录 | 记录类型 | 记录值 |
| --- | --- | --- |
| www | CNAME | `<your-account>.github.io` |

如果希望 `www.guizhufeng.com` 自动跳转到 `guizhufeng.com`，在 GitHub Pages 里保留 Custom domain 为 `guizhufeng.com`，DNS 生效后 GitHub 会处理跳转。

## 5. 生效与验收

DNS 通常 10 分钟到数小时生效。生效后依次检查：

```bash
curl -I https://guizhufeng.com/
curl -I https://guizhufeng.com/llms.txt
curl -I https://guizhufeng.com/brand-facts.json
curl -I https://guizhufeng.com/assets/bamboo-hotpot-hero.jpg
curl -I https://guizhufeng.com/sitemap.xml
```

验收标准：

- `https://guizhufeng.com/` 正常打开首页
- GitHub Pages 显示 custom domain 已验证
- HTTPS 证书签发成功，并可勾选 Enforce HTTPS
- `https://guizhufeng.com/robots.txt` 可访问
- `https://guizhufeng.com/sitemap.xml` 可访问
- `https://guizhufeng.com/llms.txt` 可访问
- `https://guizhufeng.com/brand-facts.json` 可访问
- `https://guizhufeng.com/assets/bamboo-hotpot-hero.jpg` 可访问
- 页面源代码包含 JSON-LD Schema

## 6. 上线后建议

- 在百度搜索资源平台提交 `https://guizhufeng.com/sitemap.xml`
- 在 360、搜狗、神马等国内搜索平台提交站点
- 用百度统计或腾讯云分析接入访问数据
- 后续补充证书扫描件、工厂实拍、产品实拍和真实案例页
