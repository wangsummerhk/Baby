# 屁宝学业生涯 · PWA + JSONBin 云同步

手机、电脑都能用的宝宝择校记录工具，数据**免注册**自动在多端同步。

## 功能
- 学校基本信息 / 报名时间区间 / 授课语言多选 / 状态机
- 宝宝信息卡片（出生年月日 + 16 个入学阶段自动算年龄）
- 反馈时间线 / 重要事项提醒
- K1 入学时间表参考
- 数据导入导出 JSON 备份
- PWA 移动端：可"添加到主屏幕"，像 App 一样使用
- **JSONBin 云同步**：多端自动同步，**免注册 / 免登录**

## 部署到 GitHub Pages

### 1. 创建 GitHub 仓库
- 在 https://github.com/new 创建一个**公开**仓库（如 `Baby`），不要勾选 Add README

### 2. 上传文件

**方法 A：网页拖拽**（适合小白）
1. 仓库页面 → **Add file → Upload files**
2. 把 `school-tracker.html` 和 `README.md` 拖入
3. 点 **Commit changes**
4. `.gitignore` 通过 **Add file → Create new file** 输入文件名 `.gitignore` 创建

**方法 B：命令行**（如果本地有 git）
```bash
cd 项目目录
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin https://github.com/你的用户名/Baby.git
git push -u origin main
```

### 3. 开启 GitHub Pages
1. 仓库 → **Settings** → 左侧 **Pages**
2. Source 选 **Deploy from a branch**
3. Branch 选 **main**，目录选 **/ (root)**，点 Save
4. 等 1-2 分钟，刷新页面会显示访问地址：
   `https://你的用户名.github.io/Baby/school-tracker.html`

### 4. 开启云同步（免注册！）

**在第一台设备（比如电脑）上：**
1. 打开 GitHub Pages 链接
2. 点顶栏 **☁** 按钮 → 点 **开启自动同步**
3. 几秒后状态变"已同步" ✅
4. 弹层里会显示一个 **16 位 binId**（如 `6840a1c88961e97a501b1f3c`），点旁边 **复制**

**在第二台设备（比如手机）上：**
1. 用手机浏览器打开同一个 GitHub Pages 链接
2. 点顶栏 **☁** → 点 **绑定已有云端**
3. 把电脑上的 binId 粘贴进去 → 确认
4. 几秒后状态变"已同步" ✅ — 数据已经同步过来了

之后任何一端修改，**另一端打开页面时自动同步**（每次改动后约 1 秒）。

## 离线 / 本地使用
不配云同步也能用 — 数据保存在浏览器 localStorage。配合 PWA 添加到主屏幕，体验和云同步版本一样，只是多端不互通。

## 文件清单
- `school-tracker.html` — 单文件应用（HTML + CSS + JS + 图标）
- `README.md` — 本文档
- `.gitignore` — 排除 WorkBuddy 工作目录

## 技术栈
- 纯 HTML + CSS + 原生 JS（无构建步骤）
- [JSONBin.io](https://jsonbin.io) REST API（云同步，免费层 10K 存储/100K 请求/月）
- 移动端 viewport-fit + safe-area-inset（PWA 全屏沉浸）
