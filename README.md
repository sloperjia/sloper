# MicroSIP 3.21.6 - 外呼限制版本

## 概述

这是基于官方 MicroSIP 3.21.6 的修改版本，添加了**外呼限制功能**。

## 主要修改

### ✨ 新增功能
- **外呼限制控制**: 可通过配置文件禁止发起外呼电话
- **默认禁止外呼**: 默认配置下禁止外呼，提高安全性
- **来电功能保持**: 不影响接听来电和通话控制功能
- **配置持久化**: 设置自动保存到INI配置文件

### 📝 配置方法

在 `MicroSIP.ini` 文件中的 `[Settings]` 部分添加：

```ini
[Settings]
disableOutgoing=1   ; 1 = 禁用外呼 (默认), 0 = 允许外呼
```

**配置文件位置**:
- 安装模式: `%APPDATA%\\MicroSIP\\MicroSIP.ini`
- 便携模式: 程序目录下的 `MicroSIP.ini`

### 🔧 技术实现

修改的文件：
1. **settings.h**: 添加 `disableOutgoing` 配置项
2. **settings.cpp**: 添加INI读取/写入逻辑
3. **mainDlg.cpp**: 在 `MakeCall` 函数中添加外呼检查
4. **MessagesDlg.cpp**: 在 `CallStart` 函数中添加外呼检查

## 使用场景

- **企业环境**: 限制员工外呼，仅允许接听
- **客服中心**: 控制外呼权限
- **安全考虑**: 防止意外的外呼操作

## 编译要求

- **开发环境**: Visual Studio 2022 或 2019
- **平台**: Windows 10 或更高版本
- **依赖**: PJSIP 库、MFC 框架
- **架构**: x64

## 编译步骤

1. 安装 Visual Studio 2022 Community
2. 安装 "使用 C++ 的桌面开发" 工作负载
3. 配置 PJSIP 库依赖
4. 打开 `microsip.vcxproj` 项目文件
5. 编译 Release x64 配置

## 功能特性

- ✅ 接听来电正常
- ✅ 通话控制功能完整
- ✅ 消息功能不受影响
- ❌ 禁止发起外呼电话
- 📱 用户友好的提示信息

## 许可证

基于 GNU General Public License v2.0
原始代码: Copyright (C) 2011-2024 MicroSIP (http://www.microsip.org)