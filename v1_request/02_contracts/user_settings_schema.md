# User Settings Schema (数据契约)

本模型定义了网页端设置面板背后的存储结构。为了支撑产品层定义的状态机与异常边缘处理，契约内部严格规定了特定字段的枚举边界与异常态字典。

## JSON Schema 示例与状态定义

```json
{
  "user_id": "usr_9a8b7c6d5e4f3g",
  
  // 【标注给 Dev 团队】: 下方 profile 和 storage 如果在系统中有全局的 GET /user/profile 接口，
  // 请在此处注明并链接至全局契约，避免冗余和数据不一致。如果是随 Settings 一并下发，请补齐具体字段。
  "user_profile": {
    "name": "Tonya Zhang",
    "email": "tonyadesign@gmail.com",
    "avatar_url": null
  },
  "storage_quota": {
    "used_bytes": 9878424780,
    "total_bytes": 10737418240,
    "plan_tier": "free"
  },
  
  "sync_data_preferences": {
    // 【状态限制】允许枚举: 7, 30, null。null 对应前端的 "Forever" (系统默认值)
    "recording_cloud_retention_days": null
  },
  
  "privacy_and_security": {
    // 【强制要求】新建账号或设备接入时，此值严格默认为 false
    "data_training_opt_in": false
  },
  
  "export_integrations": {
    // 【格式限制】允许枚举: "markdown", "pdf", "txt"
    "default_destination": "notion",
    "default_format": "markdown",
    "connections": {
      "notion": {
        // 【核心状态机】
        // "connected": 正常连通。
        // "disconnected": 未绑定，空状态。
        // "token_expired": [异常边缘态] Token由于第三方安全策略失效，前端需捕获此状态唤起重授权流程。
        "status": "connected",
        "last_synced": "2026-06-15T10:00:00Z"
      }
    }
  }
}
```

