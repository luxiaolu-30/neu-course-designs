# MFC_CS —— 密码学实验系统

基于 MFC 的 C/S 架构密码学实验系统，作为密码学课程设计的可视化演示工具，分为客户端 (`system_client`) 与服务端 (`system_server`) 两个 Visual Studio 项目。

---

## 功能概述

系统覆盖主流密码学算法的分类演示与交互式加解密：

- **古典密码**：Playfair 等经典密码算法
- **流密码**：RC4 流加密
- **分组密码**：分组加密算法（含工作模式）
- **公钥密码**：RSA 等公钥加密算法
- **密钥协商**：Diffie-Hellman (DH)
- **哈希算法**：MD5

每个算法模块对应独立的 MFC 对话框（`C*Dlg`），便于分模块演示与测试。

---

## 技术栈

- **语言**：C++
- **框架**：MFC (Microsoft Foundation Classes)
- **IDE**：Visual Studio（项目文件 `.sln` + `.vcxproj`）
- **架构**：C/S（Client/Server）
- **平台**：Windows

---

## 项目结构

```
MFC_CS/
├── system_client/                 # 客户端项目
│   ├── CBlockDlg.cpp/.h            # 分组密码对话框
│   ├── CCdhDlg.cpp/.h              # DH 密钥协商对话框
│   ├── CClassicalDlg.cpp/.h        # 古典密码对话框
│   ├── CDisplayView.cpp/.h         # 显示视图
│   ├── CMd5Dlg.cpp/.h              # MD5 对话框
│   ├── CPublicKeyDlg.cpp/.h        # 公钥密码对话框
│   ├── CSelectView.cpp/.h          # 算法选择视图
│   ├── CStreamDlg.cpp/.h           # 流密码对话框
│   ├── MainFrm.cpp/.h              # 主框架窗口
│   ├── blockcipher.cpp             # 分组密码实现
│   ├── classicalcipher.cpp         # 古典密码实现
│   ├── streamcipher.cpp            # 流密码实现
│   ├── publickey.cpp               # 公钥密码实现
│   ├── dh.cpp                      # Diffie-Hellman 实现
│   ├── md5.cpp                     # MD5 实现
│   ├── playfair.cpp                # Playfair 算法实现
│   ├── allin.h                     # 公共头文件
│   ├── pch.h / pch.cpp             # 预编译头
│   ├── framework.h / targetver.h   # 框架与 SDK 版本
│   ├── resource.h                  # 资源头
│   ├── system_muzinan.cpp/.h       # 应用类
│   ├── system_muzinanDoc.cpp/.h    # 文档类
│   ├── system_muzinanView.cpp/.h   # 视图类
│   ├── system_muzinan.sln          # VS 解决方案
│   ├── system_muzinan.vcxproj      # VS 项目文件
│   ├── systemmuzinan.rc / .rc2     # 资源文件
│   ├── res/                        # 资源目录（bmp/ico/png 图标与背景）
│   ├── background.bmp              # 背景图
│   ├── RC4.txt                     # RC4 示例数据
│   ├── autoplain.txt               # 自动明文示例
│   ├── cpc_infile.txt              # 输入文件示例
│   ├── cpc_outfile.txt             # 输出文件示例
│   ├── md5test.txt                 # MD5 测试数据
│   └── prime.txt                   # 素数表示例
│
└── system_server/                 # 服务端项目
    ├── C*Dlg.cpp/.h                # 与客户端对应的算法对话框
    ├── MainFrm.cpp/.h
    ├── blockcipher.cpp / classicalcipher.cpp / streamcipher.cpp
    ├── publickey.cpp / dh.cpp / md5.cpp
    ├── playfair1.cpp               # Playfair 实现（服务端版本）
    ├── system_server.sln / .vcxproj
    └── res/                       # 服务端资源
```

---

## 架构说明

```
┌──────────────────────────┐         ┌──────────────────────────┐
│     system_client        │  <-->   │     system_server        │
│  (MFC 界面 + 算法调用)    │         │  (MFC 界面 + 算法实现)    │
│                          │         │                          │
│  CSelectView  → 选择算法 │         │  CSelectView → 选择算法  │
│  CClassicalDlg → 古典密码 │         │  CClassicalDlg           │
│  CStreamDlg    → 流密码   │         │  CStreamDlg              │
│  CBlockDlg     → 分组密码 │         │  CBlockDlg               │
│  CPublicKeyDlg → 公钥密码 │         │  CPublicKeyDlg           │
│  CCdhDlg       → DH 协商  │         │  CCdhDlg                 │
│  CMd5Dlg       → MD5      │         │  CMd5Dlg                 │
└──────────────────────────┘         └──────────────────────────┘
```

- **客户端**：用户在 GUI 上选择算法、输入明文/密文与密钥，触发加解密流程
- **服务端**：与客户端结构对应，承载算法实现与交互响应

---

## 构建与运行

### 依赖

- Visual Studio 2019 或更高（含 MFC 库）
- Windows SDK（项目 `targetver.h` 指定）
- 在 VS 安装器中勾选 **"使用 C++ 的桌面开发"** 工作负载，并确认包含 MFC 组件

### 编译

1. 打开 `system_client/system_muzinan.sln` 或 `system_server/system_server.sln`
2. 选择配置（Debug/Release）与平台（Win32/x64）
3. 生成解决方案（`Ctrl+Shift+B`）

### 运行

直接在 Visual Studio 中按 `F5` 调试运行，或运行生成的 `.exe`。

---

## 使用说明

1. 启动客户端或服务端程序
2. 在主界面选择要演示的密码学算法类别
3. 在对应对话框中输入明文/密钥/密文
4. 点击加/解密按钮查看结果
5. 各算法的测试数据见 `*.txt` 文件（如 `RC4.txt`、`md5test.txt`、`prime.txt`）

---

## ⚠️ 说明

- 本系统为课程设计演示用途，算法实现未做性能与安全加固，**不可用于生产环境**
- RC4、MD5 等算法在现实场景中已被认为不安全，仅作教学演示
