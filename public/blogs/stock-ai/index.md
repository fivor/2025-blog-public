今天继续给大家分享一个Github上的项目——**daily_stock_analysis**，这是一个基于 AI 大模型的 A 股自选股智能分析系统，每日自动分析并推送「决策仪表盘+大盘复盘」到企业微信/飞书/邮箱。可以在 GitHub Actions 上零成本部署，并且每日免费运行，也无需服务器，白嫖 Gemini API - Google AI Studio 提供免费额度，个人使用完全足够。

## ✨ 功能特性

### 🎯 核心功能

- **AI 决策仪表盘** - 一句话核心结论 + 精确买卖点位 + 检查清单
- **多维度分析** - 技术面 + 筹码分布 + 舆情情报 + 实时行情
- **大盘复盘** - 每日市场概览、板块涨跌、北向资金
- **多渠道推送** - 支持企业微信、飞书、邮件（自动识别）
- **零成本部署** - GitHub Actions 免费运行，无需服务器
- **白嫖 Gemini API** - Google AI Studio 提供免费额度，个人使用完全够用
- **多模型支持** - 支持 OpenAI 兼容 API（DeepSeek、通义千问等）作为备选

### 📊 数据来源

- **行情数据**: AkShare（免费）、Tushare、Baostock、YFinance

- **新闻搜索**: Tavily、SerpAPI、Bocha

- **AI 分析**:
  - 主力：Google Gemini（gemini-3-flash-preview）—— [免费获取](https://aistudio.google.com/)
  - 备选：应大家要求，也支持了OpenAI 兼容的 API（比如 DeepSeek、通义千问、Moonshot 等）

### 🛡️ 交易理念内置

- ❌ **严禁追高** - 乖离率 > 5% 自动标记「危险」
- ✅ **趋势交易** - MA5 > MA10 > MA20 多头排列
- 📍 **精确点位** - 买入价、止损价、目标价
- 📋 **检查清单** - 每项条件用 ✅⚠️❌ 标记

## 🚀 快速开始
这个项目可以选择 Github Actions/本地/Docker 三种方式部署，我当然是选择最简单且零成本的GitHub Actions部署，关键是可以 **无需服务器，每天自动运行！**

### 1. Fork 本仓库

首先是点击右上角 `Fork` 按钮，Github上的项目地址是：

[ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis)

### 2. 配置 Secrets

进入刚才 Fork 的仓库 → `Settings` → `Secrets and variables` → `Actions` → `New repository secret`，按自己的需求配置以下`secret`

**AI 模型配置：Google AI 和 OpenAI 至少配置一个**

Google AI Studio 注册以后可以获取免费的Key，用于这个项目完全足够。

![](http://img.fivor.cc/2026-01-22/aa59cc09-be67-4f09-a53a-dea477e1a338.png)

**通知渠道配置**

可同时配置多个渠道，然后全部推送，最简单的就是只配置发件人和收件人邮箱，其中需要注意的是`EMAIL_PASSWORD`是指发件人邮箱的授权码，不是登录密码。

![](http://img.fivor.cc/2026-01-22/1e4b8c9c-8923-4198-9d4c-7ee43d1b783b.png)

**其他配置**

自选股代码是必填，不然看不到决策仪表盘，另外建议配置新闻搜索的API。

![](http://img.fivor.cc/2026-01-22/6f02f724-b990-420c-8da8-33a83e71ac7c.png)

### 3. 启用 Actions

还是在Fork的仓库里，点击进入 `Actions` 标签 → 点击 `I understand my workflows, go ahead and enable them`，创建一个 Actions。

### 4. 手动测试

`Actions` → `每日股票分析` → `Run workflow` → 选择模式（三选一） → `Run workflow`

![](http://img.fivor.cc/2026-01-22/16306c2d-8eaa-41e2-ab42-51e5ecd0d521.png)

### 5. 完成！

等Actions全部完成后，就可以在配置的渠道里去看报报告了。默认是每个工作日的 **18:00（北京时间）** 自动执行。

![](http://img.fivor.cc/2026-01-22/0698126e-0b9f-40e2-aaf8-023b290a748c.png)

## 📱 推送效果

### 决策仪表盘
这里是以茅台为例，当然我没有买，我甚至都不炒股。

![](http://img.fivor.cc/2026-01-22/d1259daa-9467-4122-b40f-005c833f179a.png)


### 大盘复盘

![](http://img.fivor.cc/2026-01-22/2f8b97f7-de45-448f-8470-acee20c2443d.png)

## 写在最后

大家可以根据上述步骤搭建一个属于自己的AI智能分析器，如果觉得麻烦，也可以在下方留言或者私信，告诉我股票代码和邮箱。我后台设置好，工作日每天1900后会把 **“决策仪表盘+大盘复盘”** 发到你的邮箱。

众所周知，AI也会一本正经的胡说八道，而且我自己不炒股，所以也无法判断这个决策的准确性如何，大家试过以后也可以反馈效果如何。以上也只是纯粹的技术分享，只能作为一个简单的参考，不构成任何购买股票的推荐。