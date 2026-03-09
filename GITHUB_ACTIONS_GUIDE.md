# 会议录音助手 - Android App

## GitHub Actions 自动编译指南

### 第一步：创建 GitHub 仓库

1. 让你的朋友/同事登录 [github.com](https://github.com)
2. 点击右上角 "+" → "New repository"
3. 仓库名称填：`meeting-recorder`（或其他名字）
4. 选择 "Public"（公开）或 "Private"（私有）
5. 点击 "Create repository"

### 第二步：上传代码

**方法A - 网页上传（最简单）：**
1. 在仓库页面点击 "uploading an existing file"
2. 把本文件夹内的所有文件拖进去
3. 点击 "Commit changes"

**方法B - 命令行上传：**
```bash
cd 录音助手AndroidApp
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/用户名/meeting-recorder.git
git push -u origin main
```

### 第三步：触发编译

代码上传后，GitHub Actions 会自动开始编译：

1. 在仓库页面点击 "Actions" 标签
2. 你会看到 "Build Android APK" 工作流正在运行
3. 等待 3-5 分钟（首次编译较慢，需要下载依赖）

### 第四步：下载 APK

编译完成后：

1. 在 Actions 页面点击最新的一次运行记录
2. 页面底部找到 "Artifacts" 部分
3. 点击 "MeetingRecorder-APK" 下载
4. 解压下载的文件，里面的 `.apk` 就是安装包

### 手动触发编译

如果想重新编译（比如修改了代码）：

1. 进入仓库的 Actions 页面
2. 点击左侧 "Build Android APK"
3. 点击右侧 "Run workflow" → "Run workflow"

### 文件说明

```
录音助手AndroidApp/
├── .github/workflows/build-android.yml  # GitHub Actions 配置
├── app/
│   ├── build.gradle                     # App 构建设置
│   ├── proguard-rules.pro               # 代码混淆规则
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml      # 应用权限声明
│       │   ├── assets/
│       │   │   └── recorder.html        # 录音助手网页（核心）
│       │   ├── java/com/zhenzhen/recorder/
│       │   │   └── MainActivity.java    # 主Activity
│       │   └── res/                     # 资源文件
├── build.gradle                         # 项目构建设置
├── gradle.properties                    # Gradle 配置
├── gradlew                              # Gradle 包装脚本
├── gradle/wrapper/                      # Gradle 包装器
└── settings.gradle                      # 项目设置
```

### 常见问题

**Q: 编译失败怎么办？**
A: 点击 Actions 页面的运行记录，查看错误日志。通常是网络问题，点击 "Re-run jobs" 重试。

**Q: APK 安装不了？**
A: 需要在手机设置中开启 "允许安装未知来源应用"。

**Q: 如何更新代码？**
A: 修改代码后重新上传到 GitHub，Actions 会自动重新编译。

**Q: 可以修改应用名称吗？**
A: 修改 `app/src/main/res/values/strings.xml` 中的 `app_name`。

### 联系我们

如有问题，请提交 Issue 或联系开发者。

---
**Note**: 本应用需要麦克风和存储权限才能正常使用。
