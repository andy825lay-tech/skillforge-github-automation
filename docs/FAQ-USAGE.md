# FAQ - Usage Questions

## Getting Started

### Q: 第一個自動化任務?
```typescript
// 建立第一個 Issue
await skill.execute({
  action: 'issue.create',
  params: {
    title: '我的第一個自動化 Issue',
    body: '使用 SkillForge 建立',
    labels: ['automated']
  }
});
```

### Q: 如何查看所有功能?
A: 參閱 docs/API.md 完整 API 文件

## Best Practices

### Q: 如何組織大量 Issue?
使用標籤和里程碑：
```typescript
await skill.execute({
  action: 'issue.create',
  params: {
    title: 'Feature Request',
    labels: ['feature', 'priority-medium'],
    milestone: 'v2.0'
  }
});
```

### Q: PR 分析的最佳時機?
- PR 建立後立即分析
- Code Review 前再次分析
- 合併前最終檢查

### Q: 如何自動生成 Release Notes?
```typescript
await skill.execute({
  action: 'release.create',
  params: {
    tagName: 'v1.2.0',
    generateReleaseNotes: true
  }
});
```

## Advanced

### Q: 可以批次處理 Issue 嗎?
A: 可以！使用批次模式：
```typescript
const issues = await skill.execute({
  action: 'issue.list',
  params: { state: 'open', labels: ['bug'] }
});
// 批次處理...
```

### Q: 如何監控 Repository 健康度?
```typescript
const health = await skill.execute({
  action: 'repo.analyze',
  params: { owner: 'myorg', repo: 'myrepo' }
});
```

### Q: Webhook 觸發怎麼用?
A: Enterprise 版支援 webhook 設定，可自動觸發自動化流程

## Tips

### 💡 效率提升技巧
1. 設定 defaultOwner 和 defaultRepo 減少重複輸入
2. 使用 enableAllFeatures() 開啟所有功能
3. 建立常用任務的模板

### 💡 除錯技巧
- 使用 console.log 檢查回傳結果
- 查看 error message 了解問題
- 確認 GitHub token 權限足夠
