# FAQ - Technical Questions

## Installation

### Q: 如何安裝 SkillForge GitHub Automation?
```bash
npm install @skillforge/github-automation
```

### Q: 需要什麼版本的 Node.js?
A: Node.js v18.0 或更高版本

### Q: 支援哪些作業系統?
A: macOS、Linux、Windows (WSL)

## Configuration

### Q: 如何取得 GitHub Token?
1. 前往 GitHub Settings → Developer settings → Personal access tokens
2. 點擊 "Generate new token (classic)"
3. 勾選權限：repo、workflow、read:org
4. 產生並複製 token

### Q: License Key 在哪裡輸入?
```typescript
const config = new SkillConfigBuilder()
  .setLicenseKey('SF-GH-XXXX-XXXX-XXXX')
  .build();
```

### Q: 可以同時在多個專案使用嗎?
A: 可以！設定 defaultOwner 和 defaultRepo，或每次呼叫時指定。

## Troubleshooting

### Q: 出現 "License invalid" 錯誤?
- 確認 License Key 輸入正確
- 檢查是否超過安裝數量限制
- 聯繫客服確認 License 狀態

### Q: GitHub API rate limit?
A: 產品會自動處理 rate limiting，建議使用適當的 token 權限。

### Q: 如何更新到最新版本?
```bash
npm update @skillforge/github-automation
```
