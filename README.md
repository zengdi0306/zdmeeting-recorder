# 会议录音助手 - Android App

## 项目结构
这是一个基于 WebView 的 Android 应用，将网页版录音助手包装成原生 App。

## 构建步骤

### 方法1：使用 Android Studio（推荐）
1. 下载并安装 Android Studio
2. 打开本项目文件夹
3. 等待 Gradle 同步完成
4. 点击 "Build" → "Build Bundle(s) / APK(s)" → "Build APK(s)"
5. APK 文件将生成在 `app/build/outputs/apk/debug/` 目录

### 方法2：使用命令行（需要配置 Android SDK）
```bash
./gradlew assembleDebug
```

## 安装到手机
1. 在手机上开启"开发者选项"和"USB 调试"
2. 连接手机到电脑
3. 在 Android Studio 中点击 "Run" 按钮

或直接复制 APK 到手机安装：
```bash
adb install app/build/outputs/apk/debug/app-debug.apk
```

## 权限说明
- **录音权限**：用于录制会议音频
- **存储权限**：用于保存录音和转录文字到本地

## 注意事项
- Android 6.0+ 需要动态申请权限
- 建议使用 Android 8.0 (API 26) 以上系统以获得最佳体验
