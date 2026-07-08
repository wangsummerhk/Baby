# 屁宝学业生涯 · PWA + 云同步

手机、电脑都能用的宝宝择校记录工具，数据自动在多端同步。

## 功能
- 学校基本信息 / 报名时间区间 / 授课语言多选 / 状态机
- 宝宝信息卡片（出生年月日 + 16 个入学阶段自动算年龄）
- 反馈时间线 / 重要事项提醒
- K1 入学时间表参考
- 数据导入导出 JSON 备份
- PWA 移动端：可"添加到主屏幕"，像 App 一样使用
- LeanCloud 云同步：多端自动同步（手机 + 电脑 + 平板 = 同一份数据）

## 部署到 GitHub Pages

### 1. 注册 LeanCloud（云同步需要）
1. 打开 https://console.leancloud.app/ 注册账号
2. 控制台 → 创建应用 → 随便起个名字（如 `pibao-school`）
3. 进入应用 → 设置 → 应用凭证 → 复制 **AppID** 和 **AppKey**
4. 如果是国内版（默认），在 **设置 → 域名绑定** 页面可以看到形如 `xxx.tablet.leancloud.app` 的 API 域名，需要填到同步设置里
5. 国际版用户：AppKey 直接可用，服务器地址留空
6. 安全中心 → 服务开关 → 确认 `数据存储` 是开启状态

### 2. 上传到 GitHub
最简单的方式：用 GitHub 网页直接上传

1. 在 GitHub 上 **创建一个新仓库**，名字随意（如 `pibao-school`），**公开**（公开仓库才能用免费 GitHub Pages）
2. 在仓库页面点 **Add file → Upload files**
3. 把 `school-tracker.html` 和 `README.md` 拖进去
4. 等待上传完成 → 点 **Commit changes**

或者用命令行（如果本地装好了 git）：

```bash
cd 项目目录
git init
git add school-tracker.html README.md
git commit -m "init"
git branch -M main
git remote add origin https://github.com/你的用户名/pibao-school.git
git push -u origin main
```

### 3. 开启 GitHub Pages
1. 仓库 → **Settings** → 左侧 **Pages**
2. Source 选 **Deploy from a branch**
3. Branch 选 **main**（或 master），目录选 `/ (root)`，点 Save
4. 等 1-2 分钟，页面上方会显示你的访问地址：
   `https://你的用户名.github.io/pibao-school/school-tracker.html`

### 4. 配置云同步
1. 用电脑或手机浏览器打开上面的 GitHub Pages 链接
2. 点顶栏 **☁** 按钮 → 把刚才拿到的 **AppID** / **AppKey** 填进去 → 点 **保存并启用**
3. 等几秒，状态从"本地"变成"已同步"就说明通了
4. 在另一台设备上打开同一链接 → 填入**同样的** AppID / AppKey → 自动拉到同一份数据

> 凭证只存在本机浏览器 localStorage 里，不会上传 GitHub。安全。

## 离线/本地使用
如果不想配云同步，**直接双击打开 `school-tracker.html`** 也能用，数据保存在浏览器 localStorage。配合 PWA 添加到主屏幕，体验和云同步版本一样，只是多端不互通。

## 文件清单
- `school-tracker.html` — 单文件应用，所有功能（HTML + CSS + JS + 图标）都打包在里面
- `README.md` — 本文档

## 技术栈
- 纯 HTML + CSS + 原生 JS（无构建步骤）
- LeanCloud JS SDK 4.15.2（云同步）
- 移动端 viewport-fit + safe-area-inset（PWA 全屏沉浸）
