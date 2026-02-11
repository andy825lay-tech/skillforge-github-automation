# SkillForge GitHub Automation

🤖 **OpenClaw Skill for GitHub Automation**

讓你的 GitHub 管理工作全自動化 - Issue、PR、Release 一鍵搞定！

---

## ✨ 功能特色

| 功能 | 說明 | Lite | Pro | Enterprise |
|------|------|:----:|:---:|:----------:|
| 📋 **Issue 自動化** | 自動建立、標籤、指派 Issue | ✅ | ✅ | ✅ |
| 🔍 **PR 審查輔助** | 智能分析 PR 變更，提供審查建議 | ✅ | ✅ | ✅ |
| 🏷️ **Release 自動化** | 一鍵建立 Release，自動生成 Release Notes | ❌ | ✅ | ✅ |
| 📊 **Repo 分析** | Repository 健康度檢測與統計 | ❌ | ✅ | ✅ |
| 🔧 **自定義規則** | 自定義自動化工作流程 | ❌ | ❌ | ✅ |
| 🏢 **多 Repository** | 同時管理多個專案 | ❌ | ❌ | ✅ |

---

## 💰 價格方案（混合制）

### 🥉 Lite 版
**一次性費用：USDT $20**
- ✅ Issue 自動化
- ✅ PR 審查輔助
- ✅ 永久使用授權
- ✅ 基礎文件支援

### 🥈 Pro 版
**一次性費用：USDT $50** + **年度更新：USDT $10/年**
- ✅ 包含 Lite 所有功能
- ✅ Release 自動化
- ✅ Repo 分析功能
- ✅ 1 年免費更新
- ✅ Email 技術支援

### 🥇 Enterprise 版
**一次性費用：USDT $200** + **年度更新：USDT $50/年**
- ✅ 包含 Pro 所有功能
- ✅ 多 Repository 支援
- ✅ 自定義自動化規則
- ✅ 最多 5 台機器授權
- ✅ 優先技術支援
- ✅ 1 對 1 導入協助

---

## 🚀 快速開始

```bash
# 購買後取得安裝指令
npm install @skillforge/github-automation
```

```typescript
import { createGitHubSkill, SkillConfigBuilder } from '@skillforge/github-automation';

const config = new SkillConfigBuilder()
  .setGitHubToken('ghp_your_token')
  .setLicenseKey('SF-GH-XXXX-XXXX-XXXX')
  .build();

const skill = createGitHubSkill();
await skill.initialize(config);
```

---

## 🎥 Demo 影片

![功能展示](./assets/demo.mp4)

---

## 📖 文件

- [常見問題 - 購買相關](docs/FAQ-PURCHASE.md)
- [常見問題 - 技術問題](docs/FAQ-TECHNICAL.md)
- [常見問題 - 使用教學](docs/FAQ-USAGE.md)
- [隱私政策](PRIVACY-POLICY.md)
- [服務條款](TERMS-OF-SERVICE.md)

---

## 📞 購買與支援

- 💬 **Telegram Bot**: [@WhiDan66bot](https://t.me/WhiDan66bot)
- 📧 **Email**: support@skillforge.dev

**付款方式**: 僅接受 USDT (TRC-20)

---

## 📄 License

本產品為商業軟體，需購買授權後使用。
詳見 [服務條款](TERMS-OF-SERVICE.md)

---

**© 2026 SkillForge. All rights reserved.**
