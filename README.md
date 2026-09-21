# neu-course-designs

东北大学课程设计代码仓库 —— 收录本科期间各课程实训与课设项目的源码、文档与示例。

---

## 仓库总览

| 子项目 | 语言 / 框架 | 课程方向 | 简介 |
|--------|-------------|----------|------|
| [nursing_center](nursing_center/) | Java + Swing | 软件工程实训 | 护理中心管理系统（MVC 架构、文件持久化） |
| [sniffer-arp](sniffer-arp/) | C++ + Qt5 | 网络安全课程设计 | 数据包嗅探与 ARP/ICMP/Smurf 攻击工具 |
| [MFC_CS](MFC_CS/) | C++ + MFC | 密码学课程设计 | 密码学实验系统（C/S 架构，含客户端与服务端） |
| [machine_learn](machine_learn/) | Python + Jupyter | 机器学习课程 | 吴恩达课程练习与基础 ML Demo |

---

## 子项目导航

### 🏥 [nursing_center](nursing_center/) —— 护理中心管理系统

基于 Java Swing 的桌面端护理中心管理系统，采用 MVC 分层架构。

- **核心功能**：患者管理、医护人员管理、评估模板/问卷管理、评估记录、登录认证
- **架构分层**：View (Swing) → Service → DAO → PO + 文件存储
- **运行入口**：[nursing_center/src/view/LoginTest.java](nursing_center/src/view/LoginTest.java)
- **详细文档**：[nursing_center/README.md](nursing_center/README.md)

### 🌐 [sniffer-arp](sniffer-arp/) —— 网络嗅探与攻击工具

基于 Qt5 + libpcap + libnet 的网络数据包嗅探与攻击工具集。

- **核心功能**：数据包嗅探、ARP 欺骗/泛洪、ICMP Flood、Smurf、主机扫描、IP 归属地查询
- **运行平台**：Linux（主要）/ Windows（需手动配置库路径）
- **快速启动**：`qmake muzinan.pro && make -j$(nproc) && sudo ./muzinan`
- **详细文档**：[sniffer-arp/README.md](sniffer-arp/README.md)

> ⚠️ 攻击功能**仅用于授权测试与学习目的**，滥用责任自负。

### 🔐 [MFC_CS](MFC_CS/) —— 密码学实验系统

基于 MFC 的 C/S 架构密码学实验系统，分为客户端 (`system_client`) 与服务端 (`system_server`)。

- **核心功能**：
  - **古典密码**：Playfair 等古典密码算法
  - **流密码**：RC4 流加密
  - **分组密码**：分组加密算法（CBC 等模式）
  - **公钥密码**：RSA 等公钥算法
  - **密钥协商**：Diffie-Hellman (DH)
  - **哈希算法**：MD5
- **架构组成**：`system_client/`（客户端，含交互对话框） + `system_server/`（服务端）
- **构建方式**：使用 Visual Studio 打开 `system_muzinan.sln` / `system_server.sln` 编译
- **详细文档**：[MFC_CS/README.md](MFC_CS/README.md)

### 🤖 [machine_learn](machine_learn/) —— 机器学习笔记与 Demo

吴恩达机器学习课程的练习实现，以及若干深度学习基础 Demo。

- **主题涵盖**：线性回归、逻辑回归、梯度提升（LightGBM）、图像分类（CNN）、文本分类（NLP）、正则化（TensorFlow/Keras）
- **运行方式**：`jupyter notebook` 打开 `basic/` 下的各 Notebook
- **详细文档**：[machine_learn/README.md](machine_learn/README.md)

---

## 目录结构

```
neu-course-designs/
├── nursing_center/        # 护理中心管理系统（Java Swing）
│   ├── src/               # 源代码（po/dao/service/view/utils）
│   ├── data/              # TXT 数据文件
│   └── README.md
│
├── sniffer-arp/           # 网络嗅探与攻击工具（C++ Qt5）
│   ├── src/               # 源代码
│   ├── include/           # 头文件
│   ├── img/               # 界面截图
│   ├── muzinan.pro        # qmake 项目文件
│   └── README.md
│
├── MFC_CS/                # 密码学实验系统（C++ MFC）
│   ├── system_client/     # 客户端（含古典/流/分组/公钥密码、DH、MD5 对话框）
│   ├── system_server/     # 服务端
│   └── README.md
│
├── machine_learn/         # 机器学习练习（Python/Jupyter）
│   ├── basic/             # 线性/逻辑回归、梯度提升、图像/文本分类、正则化
│   └── README.md
│
├── .gitignore
└── README.md              # 本文件
```

---

## 克隆与使用

```bash
git clone https://github.com/<your-username>/neu-course-designs.git
cd neu-course-designs
```

各子项目的依赖、构建与运行步骤请参见对应目录下的 README。

---

## 开发约定

- **分支策略**：`main` 保留稳定版本，新功能在特性分支开发
- **代码风格**：各子项目沿用其语言社区规范（Java / C++ / Python）
- **`.gitignore` 覆盖范围**：
  - AI 工具配置（`.claude/`、`.codex/`、`.qoder/`、`.qwen/`、`.trae/`、`openspec/` 等）
  - IDE 配置（`.idea/`、`.vscode/`、`*.iml`、`.vs/`、`*.suo`、`*.user`）
  - Java 构建产物（`*.class`、`*.jar`、`out/`、`build/`）
  - Qt/C++ 构建产物（`*.o`、`*.exe`、`build-*/`、`*.pro.user`）
  - Visual Studio / MFC 构建产物（`Debug/`、`Release/`、`*.pdb`、`*.ilk`、`ipch/`、`*.tlog`、`*.aps` 等）
  - Python 缓存与虚拟环境（`__pycache__/`、`.venv/`、`venv/`、`.pytest_cache/`、`.ipynb_checkpoints/`）
  - 操作系统文件（`.DS_Store`、`Thumbs.db`）

---

## 许可证

本仓库代码仅用于学习交流，遵循学校课程相关规定。
