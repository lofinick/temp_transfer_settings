# Transfer Settings: 第一版产品需求

本 request 记录第一版本的 Cuneflow Transfer Settings 产品需求。

## 需求背景与核心原则

Transfer Settings 不应仅仅是一个杂项配置页，而应该承担“让用户控制会议工作流和数据生命周期”的中心角色。

- 优先保证账号与设备状态清楚
- 确保会议数据同步可理解
- 录音和隐私边界明确
- AI 输出的默认偏好可控
- 导出/分享路径顺畅

本需求定义了 Settings 的核心信息架构和功能拆解，以及网页端交互界面设计。

- [01_product/overview.md](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/01_product/overview.md) - 信息架构与软硬件设置边界划分。
- [01_product/user_stories.md](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/01_product/user_stories.md) - 核心用户场景与系统协同体验描述。
- [02_contracts/user_settings_schema.md](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/02_contracts/user_settings_schema.md) - 设置项的后端数据交互和存储 JSON 模型契约。
- [03_interface/settings_prototype.html](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/03_interface/settings_prototype.html) - 基于现有设计的 Settings HTML 高保真交互原型。
- [03_interface/interaction_states.md](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/03_interface/interaction_states.md) - 交互状态、异常卡片视觉与响应式降级规范。
- [04_checks/qa_guidelines.md](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/04_checks/qa_guidelines.md) - 核心验收边界（隔离性测试、UI保真度与空状态）。
- [presentation/prd.html](file:///Users/nickmu/claudecode/00workspace/active/cuneflow/cuneflow_edf/edfs/transfer_settings/staging/requests/v1_request/presentation/prd.html) - 需求可视化呈现，极简设计的团队可读版 PRD。
