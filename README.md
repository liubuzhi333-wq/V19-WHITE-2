# V19 Stable · 37.5℃ 数字温控系统（Android Native）

这是可直接上传至 GitHub 仓库根目录的完整 Android 工程源代码（不包含 GitHub Actions Workflow）。

## 此版界面规则

- 四个功能区域（3D动态展示、热力分析、恒温科技、温度分布）的原有面板颜色、几何尺寸和内部设计保持不变。
- 四个功能区域外的背景为纯白色 `#FFFFFF`，外部标题文字使用深灰蓝色 `#414C54`。
- 原 `36.5` 显示文案已统一改为 `37.5`（包括中英文标题、功能说明和温度色标）。
- 保留原始 V19 的媒体资源、旋转动画、热力图、按钮、触控缩放、屏幕常亮和开机自启代码。

## GitHub 上传方法

1. **先解压此 ZIP**，不要将 ZIP 原文件直接上传到 GitHub 仓库。
2. 打开 GitHub 仓库，上传解压得到的内容（`app/`、`build.gradle.kts`、`gradle.properties`、`settings.gradle.kts`、`README.md`、`.gitignore`）。
3. 所有内容都必须在**仓库根目录**：仓库根目录下应直接存在 `app/build.gradle.kts` 和 `settings.gradle.kts`，不能多一层工程文件夹。
4. 上传并提交至仓库默认分支。然后在仓库根目录自行创建 `.github/workflows/build-apk.yml`。
5. 你的 Actions 工作流需先安装 JDK 17、Android SDK、Gradle 8.9，再执行 `gradle :app:assembleDebug --stacktrace`。
6. Debug APK 默认输出位置：`app/build/outputs/apk/debug/app-debug.apk`。

本工程未内置 Gradle Wrapper（与原始 V19 保持一致），需要使用工作流安装的 Gradle 8.9。

## 工程结构

```text
app/
  build.gradle.kts
  src/main/
    AndroidManifest.xml
    assets/media/             # 120帧模型源素材、Animated WebP、4幅热力图
    java/com/liufy/thermaldisplay/
    res/values/
build.gradle.kts
settings.gradle.kts
gradle.properties
README.md
.gitignore
```

## 验证说明

ZIP 结构、资源文件一致性、温度文案扫描及 XML 解析已进行静态检查。尚未使用 Android SDK 进行实际 APK 编译，也未在实机上运行测试；构建结果以 GitHub Actions 为准。
