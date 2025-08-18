---
title: 其他配置说明
createTime: 2025/08/17 17:21:41
permalink: /config/other-config/
---

**其他配置说明**

除了站点、导航栏和个人资料配置外，Mizuka 还提供了其他几种配置选项，包括许可证、代码块和评论系统。

## 许可证配置

许可证配置位于 `src/config.ts` 文件中的 `licenseConfig` 对象，控制文章底部的许可证显示。

```typescript
export const licenseConfig: LicenseConfig = {
  enable: true,                   // 是否启用许可证显示
  name: "CC BY-NC-SA 4.0",      // 许可证名称
  url: "https://creativecommons.org/licenses/by-nc-sa/4.0/", // 许可证链接
};
```

- `enable`：设置为 `false` 可隐藏文章底部的许可证信息
- `name`：显示的许可证名称
- `url`：许可证详情页面的链接

## 代码块配置

代码块配置位于 `src/config.ts` 文件中的 `expressiveCodeConfig` 对象，控制代码块的显示样式。

```typescript
export const expressiveCodeConfig: ExpressiveCodeConfig = {
  // 注意：某些样式（如背景色）已被覆盖，请参见 astro.config.mjs 文件
  // 请选择深色主题，因为此博客主题目前仅支持深色背景
  theme: "github-dark",  // 代码块主题
};
```

- `theme`：代码块的语法高亮主题
  - 建议使用深色主题，因为 Mizuka 主题目前仅支持深色背景
  - 可选主题包括：`github-dark`、`dracula`、`one-dark` 等

## 评论系统配置

评论系统配置位于 `src/config.ts` 文件中的 `commentConfig` 对象，控制文章底部的评论系统。

```typescript
export const commentConfig: CommentConfig = {
  enable: false,  // 是否启用评论功能
  twikoo: {
    envId: "https://app.twikoo.js.org", // Twikoo 环境 ID
  },
};
```

- `enable`：设置为 `true` 启用评论功能
- `twikoo.envId`：Twikoo 评论系统的环境 ID
  - 需要先在 [Twikoo](https://twikoo.js.org/) 上创建环境并获取环境 ID

### 启用评论系统

要启用评论系统，请按以下步骤操作：

1. 在 [Twikoo](https://twikoo.js.org/) 上创建环境并获取环境 ID
2. 将 `enable` 设置为 `true`
3. 将 `twikoo.envId` 更新为您的环境 ID

```typescript
export const commentConfig: CommentConfig = {
  enable: true,
  twikoo: {
    envId: "https://your-env-id.vercel.app", // 替换为您的环境 ID
  },
};
```

## 公告功能配置说明

```typescript
export const announcementConfig: AnnouncementConfig = {
	enable: true, // 启用公告功能
	title: "Announcement", // 公告标题
	content: "Welcome to my blog! This is a sample announcement.", // 公告内容
	closable: true, // 允许用户关闭公告
	link: {
		enable: true, // 显示链接按钮
		text: "Learn More", // 链接文本
		url: "/about/", // 链接地址
		external: true, // 是否显示外部链接按钮
	},
};

```

- `enable`：设置为 `false` 可隐藏公告
- `title`：公告标题
- `content`：公告内容
- `closable`：设置为 `true` 可允许用户关闭公告
- `link.enable`：设置为 `true` 可显示链接按钮
- `link.text`：链接按钮文本
- `link.url`：链接按钮 URL
- `link.external`：设置为 `true` 可显示外部链接标记按钮


## 悬浮音乐播放器配置说明
1.首先在配置文件将 `enable` 设置为 `true`
```typescript
export const musicPlayerConfig: MusicPlayerConfig = {
	enable: true, // Enable music player feature
};
```

2.在`src/components/widget/MusicPlayer.svelte`里面的播放列表添加曲目,添加曲目需要向上迭代ID

```typescript
export const announcementConfig: AnnouncementConfig = {
	enable: true, // 启用公告功能
	title: "Announcement", // 公告标题
	content: "Welcome to my blog! This is a sample announcement.", // 公告内容
	closable: true, // 允许用户关闭公告
	link: {
		enable: true, // 显示链接按钮
		text: "Learn More", // 链接文本
		url: "/about/", // 链接地址
		external: true, // 是否显示外部链接按钮
	},
};
```