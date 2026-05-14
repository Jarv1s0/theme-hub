# Theme Hub

RouteX / Mihomo Party 主题仓库。

本仓库用于集中维护可下载的 CSS 主题文件。RouteX 会从 `latest` Release 下载 `themes.zip`，解压后在外观设置中展示可选主题。

## 使用方式

在 RouteX 中打开：

1. 进入 `设置`。
2. 打开 `外观`。
3. 点击 `获取主题`。
4. 在主题下拉框中选择需要的主题。

主题文件来自：

```text
https://github.com/Jarv1s0/theme-hub/releases/latest/download/themes.zip
```

## 新增主题

把新的 CSS 文件放到 `themes/` 目录，文件名建议使用英文和连字符，例如：

```text
themes/Signal-Core.css
```

主题首行注释会作为显示名称：

```css
/* Signal Core */
```

`--heroui-*` 颜色变量必须使用 HSL 三段值，不要写 `hsl(...)`、HEX、RGB 或 CSS 颜色名。

```css
/* 主题名 */

.light,
[data-theme='light'] {
  --heroui-primary: 186 86% 38% !important;
  --heroui-secondary: 42 76% 43% !important;
}

.dark,
[data-theme='dark'] {
  --heroui-primary: 184 92% 58% !important;
  --heroui-secondary: 46 88% 62% !important;
}
```

可以额外覆盖应用级选择器，用于统一主界面、侧边栏、卡片和悬浮窗。

```css
.main {
  background: var(--custom-main-background) !important;
}

.side,
.main .content .bg-content1 {
  background: var(--custom-side-background) !important;
}

.floating-bg {
  background: var(--custom-floating-background) !important;
}
```

## 发布机制

推送到 `main` 后，GitHub Actions 会自动：

1. 将 `themes/` 打包成 `themes.zip`。
2. 更新 `latest` tag。
3. 覆盖发布 `latest` Release 中的 `themes.zip`。

RouteX 下一次点击 `获取主题` 时会下载最新主题包。
