# 护理中心管理系统 (Nursing Center)

基于 Java Swing 的桌面端医院/护理中心管理系统，采用 MVC 架构开发，为学校实训项目。

---

## 功能概述

本系统实现了护理中心的核心业务管理功能：

- **患者管理**：患者信息的增删改查
- **医护人员管理**：员工信息管理
- **评估模板管理**：预览模板与评估模板的维护
- **评估问卷管理**：问题与问卷内容管理
- **评估记录管理**：护理评估记录的存储与查看
- **登录认证**：用户登录验证

---

## 技术栈

- **语言**：Java
- **GUI 框架**：Java Swing
- **架构模式**：MVC（Model-View-Controller）
- **数据存储**：文件 I/O（TXT 文件持久化）
- **IDE**：IntelliJ IDEA（`.iml` 项目文件）

---

## 运行环境

- JDK 8 或更高版本
- IntelliJ IDEA（推荐）或其他 Java IDE

---

## 项目结构

```
nursing_center/
├── src/
│   ├── po/                    # Model —— 持久化对象（实体类）
│   │   ├── People.java            # 人员基类
│   │   ├── Patient.java           # 患者
│   │   ├── Staff.java             # 医护人员
│   │   ├── Master.java            # 管理员/登录用户
│   │   ├── Question.java          # 问题
│   │   ├── Template.java          # 模板
│   │   ├── PreviewTemplate.java   # 预览模板
│   │   └── Record.java            # 评估记录
│   │
│   ├── dao/                   # DAO 接口 —— 数据访问层
│   │   ├── PatientDao.java
│   │   ├── StaffDao.java
│   │   ├── QuestionDao.java
│   │   ├── TemplateDao.java
│   │   ├── PreviewTemplateDao.java
│   │   └── RecordDao.java
│   │
│   ├── daoimpl/               # DAO 实现 —— 文件 I/O 实现
│   │   ├── PatientDaoimpl.java
│   │   ├── StaffDaoimpl.java
│   │   └── ...
│   │
│   ├── service/               # Service 接口 —— 业务逻辑层
│   │   ├── PatientService.java
│   │   ├── StaffService.java
│   │   └── ...
│   │
│   ├── serviceimpl/           # Service 实现
│   │   ├── PatientServiceimpl.java
│   │   ├── StaffServiceimpl.java
│   │   └── ...
│   │
│   ├── view/                  # View —— Swing 界面层
│   │   ├── LoginTest.java         # 登录界面
│   │   ├── Patients.java          # 患者管理界面
│   │   ├── Staffs.java            # 员工管理界面
│   │   ├── Questions.java         # 问题管理界面
│   │   ├── AddNewPatient.java     # 新增患者
│   │   ├── ModifyPatient.java     # 修改患者
│   │   └── ...
│   │
│   ├── utils/                 # 工具类
│   │   └── Tools.java
│   │
│   └── images/                # 图片资源
│       ├── login.jpg
│       └── login1.jpg
│
├── data/                      # 数据存储（TXT 文件）
│   ├── patient.txt
│   ├── staff.txt
│   ├── question.txt
│   ├── template.txt
│   ├── previewTemplate.txt
│   └── record.txt
│
└── NEUEDU.iml                 # IntelliJ IDEA 项目文件
```

---

## 架构说明

### MVC 分层

```
┌──────────────────────────────────────────────┐
│              View  (src/view/)                │
│    Swing 界面 —— 用户交互与数据展示           │
└──────────────────────────────────────────────┘
                      ↓ 调用
┌──────────────────────────────────────────────┐
│           Service  (src/service/)             │
│    业务逻辑层 —— 处理业务规则与数据校验        │
└──────────────────────────────────────────────┘
                      ↓ 调用
┌──────────────────────────────────────────────┐
│             DAO  (src/dao/)                   │
│   数据访问层 —— 文件读写（TXT 持久化）         │
└──────────────────────────────────────────────┘
                      ↓ 操作
┌──────────────────────────────────────────────┐
│          PO (src/po/)  +  data/              │
│   实体类（Model）+ TXT 数据文件               │
└──────────────────────────────────────────────┘
```

- **PO（Persistent Object）**：实体类，映射数据结构
- **DAO（Data Access Object）**：定义数据访问接口，`daoimpl` 提供基于文件 I/O 的实现
- **Service**：业务逻辑接口与实现，连接 View 和 DAO
- **View**：Swing 界面类，每个功能模块对应一个 JFrame/JPanel

---

## 运行方式

1. 用 IntelliJ IDEA 打开项目根目录
2. 确保已配置 JDK（项目兼容 JDK 8+）
3. 运行 `src/view/LoginTest.java` 启动登录界面

> **注意**：数据文件位于 `data/` 目录下，运行时需确保工作目录为项目根目录，否则文件路径可能无法正确解析。

---

## 数据存储

系统使用 TXT 文件作为简易持久化存储，每个实体对应一个文件：

| 文件 | 内容 |
|------|------|
| `data/patient.txt` | 患者信息 |
| `data/staff.txt` | 医护人员信息 |
| `data/question.txt` | 评估问题 |
| `data/template.txt` | 评估模板 |
| `data/previewTemplate.txt` | 预览模板 |
| `data/record.txt` | 评估记录 |
