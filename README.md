# Capture Tool

**Capture Tool** 是一款 Cadence Capture CIS 插件工具，致力于提升原理图绘制效率和版图效果。

**Capture Tool** is a Cadence Capture CIS plugin designed to improve schematic drawing efficiency and layout quality.

> 当前发布版本 / Current release: **V1.1** · 支持 / Supported: Cadence 16.x, 17.x, 22.1
>
> 发现 Bug 请反馈至 / Please report bugs to: yuanyuan.ou1@outlook.com

---

## 目录 / Table of Contents

- [简介 / Introduction](#简介--introduction)
- [安装 / Installation](#安装--installation)
- [功能总览 / Features Overview](#功能总览--features-overview)
- [功能说明 / Features](#功能说明--features)
  - [放置 Off-Page / Place Off-Page](#1-放置-off-page--place-off-page)
  - [字体颜色设置 / Font Color Setting](#2-字体颜色设置--font-color-setting)
  - [放置 Net Array / Place Net Array](#3-放置-net-array--place-net-array)
  - [NetAlias 功能 / NetAlias](#4-netalias-功能--netalias)
  - [格式刷 / Format Painter](#5-格式刷--format-painter)
  - [上件属性 / Assembly (Solder) Property](#6-上件属性--assembly-solder-property)
  - [查找替换 / Find and Replace](#7-查找替换--find-and-replace)
  - [帮助文档 / Help](#8-帮助文档--help)
- [配置文件 / Configuration](#配置文件--configuration)
- [版本历史 / Release Notes](#版本历史--release-notes)

---

## 简介 / Introduction

Capture Tool 暂不支持原理图准确性相关功能，专注于提升绘制效率与版图效果。软件主界面分为两部分：

- **Place Off-Page**：对选中的 Wire 快捷放置 OffPage 符号
- **Formatting Tools**：字体颜色设置、批量放置 Net、放置 NetAlias、格式刷、上件属性设置、查找替换

Capture Tool does not yet provide schematic-accuracy related functions; it focuses on drawing efficiency and layout quality. The main interface is divided into two parts:

- **Place Off-Page**: quickly place OffPage symbols on selected wires
- **Formatting Tools**: font color setting, batch net placement, NetAlias placement, format painter, assembly property setting, and find & replace

## 安装 / Installation

1. 下载 `Capture Tool_Setup_1.1.exe`
   Download `Capture Tool_Setup_1.1.exe`
2. 直接执行 exe 完成安装（无需手动配置加载项）
   Run the exe directly to install (no manual add-on configuration required)
3. OrCAD 启动时默认不加载插件界面，通过菜单栏按钮加载
   The plugin UI is not loaded at OrCAD startup by default; load it via the menu bar button

> 支持 / Supported: Cadence 16.x, 17.x, 22.1。其他版本暂未验证，不保证支持。
> Other versions are not yet verified and not guaranteed to work.

---

## 功能说明 / Features

### 1. 放置 Off-Page / Place Off-Page

选中需要放置 Off-Page 的 Wire（支持单个或多个 Wire 对象），点击需要的 Off-Page 箭头按钮，软件将自动完成放置。

Select the wire(s) that need an Off-Page symbol (single or multiple wires supported), then click the desired Off-Page arrow button — placement is done automatically.

> **V1.1 优化 / Improvements in V1.1**
> - 选中 Wire 可一键改变 Offpage 箭头方向 / Change Offpage arrow direction with one click on selected wire
> - 端点处有 Offpage 以外的连接对象时不再放置 Offpage / No longer places Offpage if another connecting object exists at the endpoint

### 2. 字体颜色设置 / Font Color Setting

支持 Text 对象，如 Part 的 Value、Footprint 值、插入的 Text 说明、NetAlias、Off-Page 的 name 等。

Works on Text objects, such as Part Value, Footprint value, inserted Text notes, NetAlias, and Off-Page names.

- **单击**颜色按钮：将当前默认颜色应用到选中的 Text 对象
  **Click** the color button: apply the current default color to selected Text objects
- **双击**颜色按钮：打开颜色选择器，悬停可预览 RGB 值，单击色块完成设置并更新默认颜色
  **Double-click** the color button: open the color picker (hover to preview RGB values); clicking a swatch sets the color and updates the default

> 批量选择 Text 对象容易被 Wire 等无关对象干扰，建议右键空白区域 → Selection Filter，勾选 **Graphical Object**、**Display Properties** 和 **Net Alias**。
> Batch-selecting Text objects can be disturbed by unrelated objects like wires. It is recommended to right-click blank area → Selection Filter, and check **Graphical Object**, **Display Properties** and **Net Alias**.

### 3. 放置 Net Array / Place Net Array

批量放置 Net（WireAlias、Off-Page）。单击 **Place Net Array** 按钮打开交互窗口。

Batch-place nets (WireAlias, Off-Page). Click the **Place Net Array** button to open the dialog.

| 栏目 / Field | 说明 / Description |
|---|---|
| Head / Tail | 支持任何字符（不建议输入空格，避免产生不易察觉的单端网络）/ Any characters allowed (spaces not recommended to avoid unnoticed single-ended nets) |
| Start / End | 仅支持 ≥ 0 的整数 / Non-negative integers only；支持从小到大或从大到小 / Ascending or descending allowed |

输入规则 / Input rules:

- 允许 Head、Start、End、Tail 为空，但全为空时不执行任何操作
  Fields may be empty, but nothing happens if all are empty
- Start、End 必须同时为空或同时不为空，否则不执行任何操作
  Start and End must be both empty or both non-empty, otherwise nothing happens
- Net Type 选择 **WireAlias** 时 Offpage Type 不可用，仅 Net Type 选择 **Offpage** 时可用
  Offpage Type is only available when Net Type is **Offpage**

放置起点为鼠标最后点击的坐标。点击 **Place** 前先点击需要放置的位置即可，无需考虑位置是否在格点上——软件会自动计算就近格点，并自动识别页面为公制还是英制。

The placement origin is the last mouse-click position. Click the target position before pressing **Place** — no need to snap to grid; the tool automatically snaps to the nearest grid point and detects whether the page uses metric or imperial units.

### 4. NetAlias 功能 / NetAlias

选中需要放置 NetAlias 的 Wire，点击 **NetAlias** 按钮：

Select the wire(s), then click the **NetAlias** button:

- 对没有 NetAlias 的 Wire 放置 NetAlias
  Places a NetAlias on wires that don't have one
- 对与 Offpage 的 name 不匹配的 NetAlias，更新为与 Offpage 的 name 一致
  Updates mismatched NetAlias names to match the Offpage name

### 5. 格式刷 / Format Painter

目前仅可应用于 **Part** 对象，用于解决 Part 显示属性（位号、Value、Footprint 等）位置混乱导致页面不整洁的问题。

Currently applies to **Part** objects only. It solves messy display-property positions (reference designator, Value, Footprint, etc.).

**使用方法 / How to use:**

1. **双击**参考 Part —— 提取显示属性的相对位置、旋转位置以及 Part 本体的旋转位置（仅提取显示出来的属性，隐藏属性不会被提取）
   **Double-click** the reference Part — extract relative/rotation positions of visible display properties and the Part's own rotation (hidden properties are not extracted)
2. 选择单个或多个目标 Part，**单击**格式刷按钮应用
   Select one or more target Parts and **click** the format painter button to apply

配合 OrCAD 自带的对其（Align）功能可完成整齐排列。
Combine with OrCAD's built-in Align feature for neat arrangement.

### 6. 上件属性 / Assembly (Solder) Property

原理图中许多物料在实际贴装时并不需要上件（DNP）。为方便原理图查阅和 BOM 生成，需要为不上件物料指定特殊属性值。

Many parts in a schematic are not mounted (DNP) in actual assembly. Special property values are needed for easy review and BOM filtering.

- 单击按钮即可切换状态，支持单一或多对象：上件 ↔ 不上件
  Click the button to toggle (single or multiple objects): mounted ↔ not mounted
- 不上件的 Part 属性值设为 **NO**，本体颜色突显为绿色 RGB[0,255,0]；需要上件的设为 **YES**，保持默认颜色且不显示属性
  Not-mounted parts get value **NO** and are highlighted green RGB[0,255,0]; mounted parts get **YES**, keep default color, and the property is hidden
- 属性名默认使用 OrCAD 官方的 **Assembly**，可通过 `config.json` 修改（如 ASSEMBLY、STUFF 等）
  Default property name is OrCAD's official **Assembly**; customizable via `config.json` (e.g., ASSEMBLY, STUFF)

> **导出 BOM / BOM Export**: 上件属性需手动加入 Output 并勾选 **Keyed**，这样相同物料会按上件属性区分开，便于 BOM 维护。
> When exporting BOM, manually add the assembly property to Output and check **Keyed**, so identical parts are grouped by assembly status for easier BOM maintenance.

### 7. 查找替换 / Find and Replace

针对 WireAlias 和 OffPage Name 的重复性修改，提供比 Excel 辅助更安全便捷的方式（避免拷贝过程中顺序错乱）。

Provides a safer and more convenient way than Excel-based editing for repetitive renaming of WireAlias and OffPage names (avoiding order corruption during copy-paste).

- 点击按钮打开 **Find and Replace** 窗口：**Find what** 为被替换字段，**Replace with** 为替换后的字段
  Click the button to open the **Find and Replace** dialog: **Find what** is the text to replace, **Replace with** is the new text
- 注意被替换字段在所选网络名上的唯一性，否则会被过度替换
  Make sure the search text is unique among selected net names, otherwise over-replacement may occur
- 支持对选中的单一或多个对象进行批量替换
  Supports batch replacement on single or multiple selected objects

### 8. 帮助文档 / Help

- 不再单独提供 Help 按钮，已注册为快捷键 **F1**
  No separate Help button; registered as shortcut **F1**
- 使用方法：点击一下插件窗口聚焦，再按 F1 即可查阅帮助文档
  Click the plugin window to focus it, then press **F1** to open the help document

---

## 配置文件 / Configuration

安装目录下的 `config.json` 支持用户配置上件属性名称 `solder_prop_name`（如 `ASSEMBLY`、`STUFF` 等）。

The `config.json` file in the installation directory lets you configure the assembly property name `solder_prop_name` (e.g., `ASSEMBLY`, `STUFF`).

---

## 版本历史 / Release Notes

| 版本 / Version | 修改内容 / Changes | 日期 / Date |
|---|---|---|
| V0.1 | 首次创建 / Initial release | 2026-01 |
| V0.2 | ① 帮助文档注册为快捷键 F1，不再单独提供 Help 按钮 / Help registered as F1 shortcut, separate Help button removed<br>② 新增 Alias 放置按钮 / Added Alias placement button<br>③ 上件属性 NO 显示位置优化，固定到芯片右下角 / Optimized NO property position, fixed to bottom-right of the part<br>④ 安装方式优化，直接执行 exe 安装即可 / Simplified installation via direct exe<br>⑤ OrCAD 启动默认不再加载界面，通过菜单栏按钮加载 / UI not loaded at OrCAD startup by default, loaded via menu bar button<br>⑥ 授权方式升级，每次启动时不再重复申请授权 / Licensing upgraded, no repeated activation at startup | 2026-02 |
| V0.3 | ① 插件窗口永远置为 OrCAD 的子窗口，仅在 OrCAD 窗口内顶层显示，不覆盖其他软件窗口 / Plugin window is now an OrCAD child window, topmost only within OrCAD, never covering other applications<br>② NetAlias 放置位置优化，计算就近格点放置 / NetAlias placement snaps to nearest grid point<br>③ 适配 OrCAD 16.x 版本 / Added OrCAD 16.x support | 2026-02 |
| V1.0 | ① 安装目录新增 config.json 文件，支持用户配置上件属性名称 solder_prop_name / Added config.json for custom solder property name<br>② 自动获取 Cadence 安装路径 / Auto-detect Cadence installation path | 2026-03 |
| V1.1 | ① 所有 Offpage 按钮功能优化，选中 Wire 可一键改变 Offpage 箭头方向 / All Offpage buttons improved: change arrow direction with one click on selected wire<br>② 若端点处有 Offpage 以外的连接对象时不再放置 Offpage / No longer places Offpage when other connecting objects exist at the endpoint | 2026-05 |

---

## 反馈 / Feedback

发现 Bug 或有更好的优化、开发建议，请反馈至邮箱 **yuanyuan.ou1@outlook.com**。

For bugs, optimization ideas, or development suggestions, please email **yuanyuan.ou1@outlook.com**.
