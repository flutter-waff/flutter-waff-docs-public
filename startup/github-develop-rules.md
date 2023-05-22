
# 1. 版本号定义

| | 格式 | 定义 | 更新内容 | |
|-|-|-|-| - |
| | `1`.x.x |   主要版本号 |   基础 Flutter SDK 版本变更（升级）<br>依赖的第三方 Plugin 版本变更<br>系统兼容性变更<br>核心机制变更<br>较多新特性 |
| | x.`1`.x |   次要版本号 | 新特性<br>API 变更 |
| | x.x.`1` | 小版本号 |   Bug 修复<br>性能提升 |

# 2. Git 分支定义

## 2.1 定义

| | 分支命名 | 说明 | 时效 |
|-| - | - | - |
| | `develop` |   最新版本的开发分支 | 永久 |
| | `test` | 最新版本的测试分支（非必须） | 永久 |
| | `master` |  最新版本的发布分支 | 永久 |
| | `1.0 ` , `1.0.1 ` , `1.1 ` ... | 已发布的存量版本 | 永久 |
| | `develop_x.x.x ` , ... |  基于存量版本的开发分支 | 临时 |
| | `test_x.x.x ` , ... | 基于存量版本的测试分支（非必须） | 临时 |
| | ... | 开发人员分支 | 临时 |

## 2.2 开发人员分支的命名规则

开发人员的分支，名称中需要体现 issue 类型、编号，如下：

- Feature/#issue编号...
- Bug/#issue编号...

# 3. Issues 规则（任务发起）

## 3.1 Issues 类型

|   | 类型 | 说明 | 追加 label 描述 |
| - | - | - | - |
| 1 | Version issue | 发起新版本 | `Version` , `（版本号）`, `（优先度）` , `（目标平台）...` |
| 2 | Feature issue | 发起新特性 | `Feature` , `（版本号）`, `（优先度）` , `（目标平台）...` |
| 3 | Bug issue | 发起新故障 | `Bug` , `（版本号）`, `（优先度）` , `（目标平台）...` |

## 3.2 Labels 定义

| | 分类 | 定义 | 文本 | 颜色 |
|-| -|- |- |- |
| | 类型 | 新增版本 | `Version` | #0075ca（蓝色） |
| | 类型 | 新增功能 | `Feature` | #008672（绿色） |
| | 类型 | 新增故障 | `Bug` | #d73a4a（红色） |
| | - |- |- | |
| | 版本号 | 已发布 / 已立项的版本号 | 例如 `1.0.1` | #cfd3d7（白色） |
| | - |- |- | |
| | 优先度 | 优先度 - 低 | `Low` | #cfd3d7（白色） |
| | 优先度 | 优先度 - 中 | `Middle` | #e4e669（黄色） |
| | 优先度 | 优先度 - 高 | `Hign` | #D93F0B（橘色） |
| | 优先度 | 优先度 - 紧急 | `Urgent`  | #d73a4a（红色） |
| | - |- |- |  |
| | 目标平台 | 全部 | `All` | #cfd3d7（白色） |
| | 目标平台 | Android | `Android` | #00e082（水绿色） |
| | 目标平台 | iOS | `iOS` | #9cafb6（银灰色） |
| | 目标平台 | Windows | `Windows` | #1fa1eb（天蓝色）|
| | 目标平台 | macOS | `macOS` | #9cafb6（银灰色） |
| | 目标平台 | Linux | `Linux` | #f5c138（企鹅 Logo 黄色） |
| | 目标平台 | Web | `Web` | #e55331（HTML 5 Logo 橘红色） |
| | 目标平台 | 其他 | `Other` | #cfd3d7（白色） |

提示：同一条 issue 目标平台 label 可以追加多个

3.3 示例



# 4. 开发流程


## 4.1 最新版本

假定，以开发全新版本 4.0.0 ，为例：

| 步骤 | 工作内容 | |
|-|-|-|
| 1 | 在 Github 的 Labels 定义中 ，新增一个 `4.0.0` |  |
| 2 | 发起一个新的 Version issue ，添加 label ：`Version` 、 `4.0.0` 、 `（优先度）`、`（目标平台）` |  |
|-|-|-|
| 3 | 为每一项 Feature，发起一个单独的 Feature issue ，描述功能、添加 label ：`Feature` 、 `4.0.0` 、 `（优先度）`、`（目标平台）` |  |
| 4 | 以 `develop` 分支为主线，开发过程中，定期从分支 `develop` 中合并最新代码（仅合并、不提交） |  |
| 5 | 一项 Feature 开发 & 自测完成，提交合并至 `develop` 分支，在描述中关联对应的 issue 编号 |  |
| 6 | 完成一个 Feature，将对应的 Feature issue 状态变更为 Close |  |
|-|-|-|
| 7 | 全部 Feature 提交 & 测试完成，检查确认 `发布准备` 中的各项 |  |
| 8 | 创建新的代码分支 `4.0.0`，拉取 `develop` 最新代码，提交，在描述中关联对应的 Version issue 编号 |  |
| 9 | 将 `4.0.0` 分支，同步到 `master` 分支上 |  |
| 10 | 将对应的 Version issue 状态变更为 Close |  |

提示：
同一个 Feature 在不同的目标平台上实现，可能涉及不同的技术和人员，可以酌情拆分为多个 issue 。

## 4.2 存量版本

假定，以存量版本 3.1.0 中发现 Bug 、需要更新，为例：

| 步骤 | 工作内容 | |
|-|-|-|
| 1 | 发起一个新的 Bug issue ，描述问题、添加 label ：`Bug` 、 `3.1.0` 、 `（优先度）`、`（目标平台）` |  |
| 2 | 在 Github 的 Labels 定义中 ，新增一个：`3.1.1` |  |
| 3 | 发起一个新的 Version issue ，添加 label ：`Version` 、 `3.1.1` 、 `（优先度）`、`（目标平台）` |  |
| 4 | 新建一个代码分支 `develop_3.1.1` ，从已有 `3.1.0` 分支中拉取代码，以 `develop_3.1.1` 为开发主线 |
|-|-|-|
| 5 | 一个 Bug 修复 & 自测完成，提交合并至 `develop_3.1.1` 分支，在秒述中关联对应的 issue 编号 |  |
| 6 | 每修复一个 Bug，将对应的 Bug issue 状态变更为 Close |  |
|-|-|-|
| 7 | 全部 Bug 提交 & 测试完成，，检查确认 `发布准备` 中的各项 |  |
| 8 | 创建新的分支 `3.1.1`，拉取 `develop_3.1.1` 分支代码，提交，在描述中关联对应的 Version issue 编号 |  |
| 9 | 删除 `develop_3.1.1` 分支 |  |
| 10 | 将对应的 Version issue 状态变更为 Close |  |

# 5. 发布准备

## 5.1 更新项目描述

### 5.1.1 项目清单 - pubspec.yaml

检查和更新以下内容：

- version：

### 5.1.2 项目介绍 - README.md

检查和更新与环境、依赖、版本、功能、特性相关的描述。

### 5.1.3 更新日志 - CHANGELOG.md

在文档头部追加内容，逐条列举本次更新的内容。

标注类型：新增 [Add]、变更/移动 [Change]、更新 [Update]、修复 [Fixed]、删减 [Removed]

重要变更：用 Emoji 表情符号突出强调，如 ⚠️ 

示例：

```
## 3.1.0
* ⚠️ Support web develop
* [Change] jsondecode move to example project
* [Change] example project add the dio lib
* [Fixed] http-lib's errorCode
* [Fixed] sqflite lib move to example project

```

### 5.1.4 其他

- /example/pubspec.yaml 中的版本号

# 6. 发布

## 6.1 生成 Tag

待完善。

参考：

https://docs.github.com/zh/repositories/releasing-projects-on-github/managing-releases-in-a-repository

https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

## 6.2 发布到 pub.dev

待完善。

参考：

https://dart.dev/tools/pub/publishing

# 7. 其他

## 7.1 Bug 修复更新策略

假定，有存量版本 `1.0` , `2.0` , `2.1` , `3.0` , `3.1` ，以及开发版本 `4.0` ，在 `2.1` 中发现了 Bug ，采取以下修复和更新策略：

- 在发现 Bug 的 `2.1` 版本代码基础上，更新、发布小版本 `2.1.1`
- 然后将代码合并到最新开发版本 `4.0` 中
- 中间的其他存量版本暂不更新

## 7.2 附加组件版本更新

附加组件指 flutter-waff 主项目的附属内容：

- docs（开发文档）

- samples（示例）

- template（项目模板）

- 以及培训 PPT 等

附加组件更新策略：

- 主要版本、次要版本：涉及功能增减、API 变更，需要对应更新

- 小版本：涉及Bug修复、性能提升，不需要更新