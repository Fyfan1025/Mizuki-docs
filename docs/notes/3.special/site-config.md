---
title: 站点配置说明
createTime: 2025/08/17 17:21:41
permalink: /special/site-config/
---

**站点配置说明**

站点配置位于 `src/config.ts` 文件中的 `siteConfig` 对象，控制博客的基本信息和全局设置。

## 配置项详解

### 基本信息

```typescript
export const siteConfig: SiteConfig = {
  title: "Mizuki",        // 网站标题
  subtitle: "One demo website",  // 网站副标题
  lang: SITE_LANG,         // 网站语言，如 'en', 'zh_CN', 'ja' 等
}
```

- `title`：网站的主标题，显示在浏览器标签页和页面头部
- `subtitle`：网站的副标题，通常显示在主页横幅下方
- `lang`：网站的默认语言，影响日期格式、翻译等功能

### 主题颜色

```typescript
  themeColor: {
    hue: 210,     // 主题色的色相值，范围 0-360
    fixed: false, // 是否隐藏访客的主题色选择器
  },
```

- `hue`：主题色的色相值，可以是 0-360 之间的任何数值
  - 红色: 0
  - 青色: 200
  - 蓝绿色: 250
  - 粉色: 345
- `fixed`：设置为 `true` 时，访客将无法更改主题色

### 翻译设置

```typescript
  translate: {
    enable: true,              // 是否启用翻译功能
    service: "client.edge",   // 翻译服务，目前仅支持 client.edge
    defaultLanguage: getTranslateLanguageFromConfig(SITE_LANG), // 默认翻译语言
    showSelectTag: false,      // 是否显示语言选择下拉菜单
    autoDiscriminate: true,    // 是否自动检测用户语言
    ignoreClasses: ["ignore", "banner-title", "banner-subtitle"], // 忽略翻译的CSS类名
    ignoreTags: ["script", "style", "code", "pre"], // 忽略翻译的HTML标签
  },
```

### 横幅设置

横幅设置控制主页顶部的横幅显示：

```typescript
  banner: {
    enable: true,  // 是否启用横幅
    src: {         // 横幅图片路径
      desktop: [   // 桌面端图片数组
        "assets/desktop-banner/1.webp",
        "assets/desktop-banner/2.webp",
        // 支持多张图片，自动启用轮播
      ],
      mobile: [    // 移动端图片数组
        "assets/mobile-banner/1.webp",
        "assets/mobile-banner/2.webp",
        // 移动端专用图片
      ],
    },
    position: "center", // 图片对齐方式，支持 'top', 'center', 'bottom'
    
    carousel: {
      enable: true,    // 启用轮播功能（多图片时）
      interval: 1,     // 轮播间隔时间（秒）
    },
    
    homeText: {
      enable: true,    // 在首页显示自定义文本
      title: "Mizuki", // 首页横幅主标题
      subtitle: [      // 副标题数组，支持多个文本
        "One demo website",
        "Carousel Text1",
        "Carousel Text2",
      ],
      typewriter: {
        enable: true,     // 启用打字机效果
        speed: 100,       // 打字速度（毫秒）
        deleteSpeed: 50,  // 删除速度（毫秒）
        pauseTime: 2000,  // 完整显示后的暂停时间（毫秒）
      },
    },
    
    credit: {
      enable: false,    // 显示横幅图片来源文本
      text: "Describe", // 来源文本
      url: "",          // 可选：原作品或作者页面链接
    },
  },
```

#### 横幅配置详解

- **图片路径**：相对于 `/src` 目录，如果以 `/` 开头则相对于 `/public` 目录
- **轮播功能**：当图片数组长度大于1时自动启用轮播
- **响应式设计**：桌面端和移动端可使用不同的图片
- **打字机效果**：副标题支持动态打字机效果，可配置速度和暂停时间

### 目录设置

```typescript
  toc: {
    enable: true, // 是否启用目录功能
    depth: 3,     // 目录深度，1-6，1表示只显示h1标题
  },
```

- `enable`：设置为 `false` 可禁用文章目录功能
- `depth`：控制目录显示的标题层级深度
