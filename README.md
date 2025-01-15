# glados-auto
# GLaDOS-Checkin-Worker

🚀 基于 Cloudflare Workers 的 GLaDOS 自动签到脚本

## 功能特点

- ✨ 全自动签到，无需服务器
- 📱 美观的响应式 Web 界面
- 👥 支持多账号管理
- 📨 签到结果推送（PushPlus）
- 💾 签到记录持久化存储
- ⏰ 定时自动执行
- 🔄 支持手动触发签到

## 部署步骤

### 1. 配置 Cloudflare Workers

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 创建新的 Worker
3. 复制本项目代码到 Worker 编辑器中

### 2. 创建 KV 命名空间

```bash
# 在 Workers & Pages -> KV 中创建新的命名空间
命名空间名称：GLADOS_KV
```

### 3. 配置环境变量

在 Worker 的 Settings -> Variables 中添加：

```bash
GLADOS_COOKIE=你的GLaDOS Cookie
PUSHPLUS_TOKEN=你的PushPlus Token
```

多账号配置时使用 & 分隔 Cookie：
```
cookie1&cookie2&cookie3
```

### 4. 设置定时触发器

在 Worker 的 Triggers 中添加 Cron 触发器：
```bash
30 1 * * *    # UTC 1:30 (北京时间 9:30)
```

## 使用说明

1. 访问 Worker 地址查看签到状态
2. 点击"手动签到"按钮可立即执行签到
3. 签到结果将通过 PushPlus 推送通知
4. 可在 Web 界面查看历史记录

## 注意事项

- Cookie 获取：登录 GLaDOS 后获取
- 时区设置：Cron 表达式使用 UTC 时间（比北京时间慢 8 小时）
- 免费额度：Cloudflare Workers 每天 100,000 次免费请求
- 运行频率：建议每天执行一次即可

## 更新日志

- 2024.01.15：初始发布
- 2024.01.16：添加响应式界面
- 2024.01.17：优化错误处理

## 相关项目

- [GLaDOS](https://github.com/glados-network/GLaDOS)
- [pushplus](http://www.pushplus.plus/)

## License

MIT License

Copyright (c) 2024 Your Name
