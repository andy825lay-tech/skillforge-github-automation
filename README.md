# SkillForge GitHub Automation

<p align="center">
  <img src="./marketing/logo-512x512.png" width="120" alt="SkillForge Logo">
</p>

<p align="center">
  <strong>🤖 专业级 GitHub 自动化管理工具</strong><br>
  让 Issue、PR、Release 管理全自动化，提升开发效率 10 倍
</p>

<p align="center">
  <a href="#-价格方案">💰 价格</a> •
  <a href="#-快速开始">🚀 快速开始</a> •
  <a href="#-功能说明">📖 文档</a> •
  <a href="#-购买流程">🛒 购买</a>
</p>

---

## ✨ 为什么选择 SkillForge？

| 痛点 | 传统方式 | SkillForge 方案 |
|------|---------|----------------|
| 手动创建 Issue | 5-10 分钟/个 | **1 秒自动完成** |
| PR 审查分析 | 人工检查代码 | **AI 智能分析变更** |
| Release 发布 | 手动填写信息 | **一键自动生成** |
| 多仓库管理 | 切换登录疲惫 | **统一界面管理** |

**适用对象**：独立开发者、技术团队、开源项目维护者

---

## 💰 价格方案

### 🥉 Lite 版 - USDT $20
**一次性购买，永久使用**

✅ Issue 自动化（创建、标签、指派）  
✅ PR 基础分析（变更统计）  
✅ 永久授权，终身免费  
✅ 基础技术支持  

❌ Release 自动化  
❌ 高级分析功能  

**适合**：个人开发者、小型项目

---

### 🥈 Pro 版 - USDT $50 + $10/年
**一次性费用 + 年度更新（可选）**

✅ 包含 Lite 所有功能  
✅ Release 自动化（一键发布）  
✅ Repository 健康度分析  
✅ Webhook 触发自动化  
✅ 1 年免费功能更新  
✅ 优先邮件技术支持  

**年度更新费 $10/年**：获取最新功能、安全更新、技术支持  
*（不续费仍可永久使用现有版本）*

**适合**：专业开发者、技术团队

---

### 🥇 Enterprise 版 - USDT $200 + $50/年
**企业级解决方案**

✅ 包含 Pro 所有功能  
✅ 多 Repository 统一管理（最多 10 个）  
✅ 自定义自动化规则  
✅ 最多 5 台设备授权  
✅ 专属技术支持通道  
✅ 1 对 1 导入协助  
✅ 优先功能定制开发  

**年度更新费 $50/年**：企业级 SLA 保障  
*（不续费仍可永久使用现有版本）*

**适合**：企业团队、大型开源项目

---

## 🛡️ 机器绑定保护

为保障您的权益，每个 License 采用 **机器指纹绑定** 技术：

- 🔒 **Lite/Pro**：绑定 1 台电脑
- 🔒 **Enterprise**：绑定最多 5 台电脑
- 🔄 **免费换机**：提供旧机器解除绑定服务
- 🚫 **防止共享**：有效防止 License 被多人共用

**换电脑流程**：在原电脑上执行解除绑定 → 在新电脑上重新激活

---

## 🚀 快速开始

### 系统要求

- Node.js 18.0+
- GitHub Personal Access Token
- 有效的 SkillForge License Key

### 安装步骤

#### 1. 获取 License Key

购买后您将收到形如 `SF-PR-XXXX-XXXX-XXXX` 的 License Key

👉 **购买方式**：Telegram [@WhiDan66bot](https://t.me/WhiDan66bot)

#### 2. 安装 Skill

```bash
# 通过 npm 安装（购买后提供安装包）
npm install ./skillforge-github-automation-1.0.0.tgz

# 或通过私有 registry
npm install @skillforge/github-automation
```

#### 3. 配置 GitHub Token

1. 访问 GitHub Settings → Developer settings → Personal access tokens
2. 点击 "Generate new token (classic)"
3. 勾选权限：
   - ✅ `repo` - 完整仓库控制
   - ✅ `workflow` - 工作流管理
4. 复制生成的 token

#### 4. 首次激活

```typescript
import { createGitHubSkill, SkillConfigBuilder } from '@skillforge/github-automation';

const skill = createGitHubSkill();

// 首次使用会自动绑定此电脑
await skill.initialize({
  githubToken: 'ghp_your_github_token_here',
  licenseKey: 'SF-PR-XXXX-XXXX-XXXX',  // 您的 License Key
  defaultOwner: 'your-github-username', // 默认仓库所有者
  defaultRepo: 'your-repo-name'         // 默认仓库名
});

console.log('✅ 激活成功！已绑定此设备');
```

**激活成功后将生成机器指纹文件**：`~/.skillforge/license.json`

---

## 📖 功能说明

### 📋 Issue 自动化

#### 创建 Issue
```typescript
// 快速创建带标签的 Issue
await skill.execute({
  action: 'issue.create',
  params: {
    title: '[Bug] 登录功能异常',
    body: '## 问题描述\n详细描述...',
    labels: ['bug', 'priority-high'],
    assignees: ['developer-name'],
    milestone: 'v2.0'
  }
});

// 返回结果
// { success: true, issueNumber: 42, url: 'https://github.com/...' }
```

#### 列出 Issue
```typescript
// 获取带筛选的 Issue 列表
const issues = await skill.execute({
  action: 'issue.list',
  params: {
    state: 'open',           // open | closed | all
    labels: ['bug', 'urgent'],
    assignee: 'developer-name',
    limit: 50
  }
});

// 返回格式化后的 Issue 数组
// [{ number, title, state, labels, url }, ...]
```

---

### 🔍 PR 审查辅助

#### 基础分析（Lite 版）
```typescript
const analysis = await skill.execute({
  action: 'pr.analyze',
  params: {
    pullNumber: 123,
    owner: 'company-org',    // 可选，默认使用初始化配置
    repo: 'project-repo'     // 可选
  }
});

// 返回结果
{
  number: 123,
  title: 'Add new feature',
  state: 'open',
  additions: 486,
  deletions: 123,
  changedFiles: 12,
  author: 'developer-name'
}
```

#### 完整分析（Pro/Enterprise 版）
```typescript
const fullAnalysis = await skill.execute({
  action: 'pr.analyze',
  params: {
    pullNumber: 123,
    detailed: true  // Pro+ 支持详细分析
  }
});

// 返回增强分析
{
  // ...基础信息
  files: [
    { filename: 'src/api.js', status: 'modified', additions: 45, deletions: 12 }
  ],
  reviewCount: 3,
  reviewStatus: 'approved',
  suggestions: ['考虑添加单元测试', '文档需要更新']
}
```

---

### 🏷️ Release 自动化（Pro/Enterprise）

```typescript
// 一键创建 Release
await skill.execute({
  action: 'release.create',
  params: {
    tagName: 'v1.2.0',
    name: 'Version 1.2.0',           // 可选，默认使用 tag 名
    generateReleaseNotes: true,       // 自动生成变更日志
    draft: false,                     // 是否为草稿
    prerelease: false                 // 是否为预发布
  }
});

// 自动生成包含 PR 列表的 Release Notes
```

---

### 📊 Repository 分析（Pro/Enterprise）

```typescript
// 获取仓库健康度报告
const health = await skill.execute({
  action: 'repo.analyze',
  params: {
    owner: 'your-org',
    repo: 'your-repo'
  }
});

// 返回综合报告
{
  score: 85,                    // 健康度评分 0-100
  stars: 1200,
  forks: 345,
  openIssues: 23,
  avgResponseTime: '2 days',    // Issue 平均响应时间
  lastUpdate: '2026-02-12',
  recommendations: ['建议关闭 5 个过时 Issue']
}
```

---

## 🔄 设备转移（换电脑）

如需更换电脑，请先在原设备上解除绑定：

```typescript
// 在原电脑上执行
await skill.transferLicense();

// 输出：✅ 解除绑定成功！您现在可以在新设备上启用此授权。
```

然后在新电脑上重新执行 [首次激活](#4-首次激活) 流程。

**注意**：
- Lite/Pro 每次只能绑定 1 台设备
- Enterprise 可同时绑定最多 5 台设备
- 解除绑定次数无限制
- 如遇问题可联系客服协助

---

## 🛒 购买流程

### 付款方式

- **仅接受**：USDT (TRC-20 网络)
- **钱包地址**：`TALc5eQifjsd4buSDRpgSiYAxUpLNoNjLD`

⚠️ **重要**：请务必使用 TRC-20 网络转账，其他网络会导致资金丢失！

### 购买步骤

1. **选择版本**：决定购买 Lite / Pro / Enterprise
2. **转账付款**：向上述地址转账对应金额
3. **保留截图**：保存转账成功截图（含交易哈希）
4. **联系客服**：
   - Telegram: [@gousmaaa](https://t.me/gousmaaa)
   - 或 Telegram Bot: [@WhiDan66bot](https://t.me/WhiDan66bot)
5. **发送信息**：
   - 付款截图
   - 您的 Email（用于接收 License）
   - 您的 Telegram ID
6. **收取 License**：24 小时内收到 License Key 和详细安装指南

### 推荐奖励计划

推荐朋友购买，**双方各得 USDT $5 回馈**！

- 购买后获得专属推荐码
- 朋友购买时提供您的推荐码
- 确认后自动发放奖励

---

## 🎁 功能对比表

| 功能 | Lite ($20) | Pro ($50+$10/年) | Enterprise ($200+$50/年) |
|------|:----------:|:----------------:|:------------------------:|
| Issue 自动化 | ✅ | ✅ | ✅ |
| PR 基础分析 | ✅ | ✅ | ✅ |
| PR 完整分析 | ❌ | ✅ | ✅ |
| Release 自动化 | ❌ | ✅ | ✅ |
| Repo 健康分析 | ❌ | ✅ | ✅ |
| 多仓库管理 | ❌ | ❌ | ✅ |
| 自定义规则 | ❌ | ❌ | ✅ |
| 设备授权数 | 1 台 | 1 台 | 5 台 |
| 年度更新 | 无需 | $10/年 | $50/年 |
| 技术支持 | 基础 | 优先邮件 | 专属通道 |

---

## 📞 技术支持

### 自助资源

- 📖 [常见问题 - 购买相关](docs/FAQ-PURCHASE.md)
- 📖 [常见问题 - 技术问题](docs/FAQ-TECHNICAL.md)
- 📖 [常见问题 - 使用教学](docs/FAQ-USAGE.md)
- 🔒 [机器绑定说明](docs/MACHINE-BINDING.md)

### 联系客服

| 渠道 | 响应时间 | 适用版本 |
|------|---------|---------|
| Telegram Bot: [@WhiDan66bot](https://t.me/WhiDan66bot) | 即时 (AI) | 所有 |
| Telegram: [@gousmaaa](https://t.me/gousmaaa) | 24 小时内 | 所有 |
| Email: support@skillforge.dev | 24-48 小时 | Pro+ |
| 专属技术支持 | 4 小时内 | Enterprise |

---

## ⚖️ 法律条款

- [隐私政策](PRIVACY-POLICY.md) - 我们如何保护您的数据
- [服务条款](TERMS-OF-SERVICE.md) - 使用协议与退款政策

---

## 🆘 常见问题

**Q: 购买后可以退款吗？**  
A: 7 天内未激活使用可申请全额退款。已激活的 License 不支持退款。

**Q: 年度更新费必须交吗？**  
A: 不是必须的。不续费仍可永久使用已购买的版本，只是无法获得新功能更新。

**Q: 可以开发票吗？**  
A: Enterprise 版本支持开具电子收据。由于采用加密货币支付，无法提供传统发票。

**Q: 我的数据安全吗？**  
A: 您的 GitHub Token 和 License 信息仅保存在本地电脑，我们不会收集或上传任何敏感数据。

**Q: 支持哪些操作系统？**  
A: 支持 macOS、Linux、Windows (WSL2)。

---

<p align="center">
  <strong>立即提升您的 GitHub 管理效率！</strong><br>
  <a href="https://t.me/WhiDan66bot">🚀 点击购买 @WhiDan66bot</a>
</p>

<p align="center">
  <sub>© 2026 SkillForge. All rights reserved.</sub>
</p>
