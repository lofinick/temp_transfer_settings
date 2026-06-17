# 交互状态与视图降级 (Interaction States)

本章节定义了 HTML 原型中无法完全呈现的动态交互状态、异常视觉和响应式适配规则，指导前端开发进行高保真还原。

## 1. 全局交互状态 (Global Interactions)

### Loading 状态 (Initial Load)
- **视觉要求**：初次进入 Settings 时，不得出现白屏或由于数据未返回导致的布局错乱。
- **骨架屏 (Skeleton)**：需使用灰色的渐变骨架屏占位，骨架屏的轮廓应与实际的 Setting Cards 和 Sidebar 菜单高度相似，并在数据返回后（或 1 秒后）采用 `opacity` 渐变平滑过渡至真实内容。

### Toast 反馈组件 (Global Toast)
- **触发场景**：针对“自动保存”机制的成功或失败反馈。
- **视觉定义**：
  - 出现在页面正上方（距离顶部 24px），层级最高 (`z-index: 9999`)。
  - **成功 (Success)**：绿色背景/边框，文案例如 `Settings saved`。停留 2 秒后消失。注：对于非高危操作可静默保存不弹成功 Toast，但失败必须弹。
  - **失败 (Error)**：红色背景/边框，文案例如 `Failed to save, please try again`。停留 4 秒后消失。同时，触发失败的开关必须进行视觉**回弹 (Bounce back)**至修改前的状态。

---

## 2. 异常态卡片视觉 (Error State Cards)

### 授权过期 (Token Expired State)
在 `Export Integrations -> Connected Apps` 区域，若接口返回 `token_expired` 状态，需渲染专属的警告卡片：
- **卡片背景**：浅橙色 (`#fff7ed`)
- **边框颜色**：橙色 (`#fed7aa`)
- **图标与标题**：红橙色警示图标，标题变为 "Notion Workspace (Action Required)"
- **文案**：`Your authorization has expired due to security policies. Please re-authenticate to continue exporting.`
- **操作按钮**：显眼的橙色主按钮 `Re-authenticate`，替代原有的设置项。

---

## 3. 响应式布局与降级 (Responsive Design)

当前的 Web 端原型主要针对桌面端设计。若要在移动设备上访问设置，需遵循以下布局降级规则：

### 侧边栏 (Sidebar) 降级
- 屏幕宽度 `< 768px` 时，左侧的 `Sidebar` (宽度 260px) **默认隐藏**。
- 顶部 Header 区域左侧新增一个“汉堡菜单 (Hamburger Icon)”。
- 点击汉堡菜单，Sidebar 从屏幕左侧以 Drawer（抽屉）形式滑出，覆盖在主内容之上，右侧出现黑色半透明遮罩 (`backdrop`)。

### 内容区 (Main Content) 降级
- `settings-container` 的内边距 (Padding) 从 `0 48px` 缩减为 `0 16px`。
- **设置项导航 (Settings Nav)**：在移动端下，不再作为左侧导航树存在，而是转变为**顶部水平滑动的 Tab Bar**，悬浮在 Header 下方。
- **Setting Cards**：内部布局从左右 Flex 布局 (Row) 降级为上下布局 (Column)，如 Toggle 开关和 Select 框被推至新的一行并靠右对齐。
