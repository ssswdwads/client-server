# 工业现场远程专家支持系统

一个使用 Qt 开发的“客户端-服务端”示例/应用。项目包含独立的服务端与客户端组件，便于本地或局域网内进行通信功能的开发与验证。



## 1. 项目简介

- 项目类型：Qt 跨平台桌面/控制台应用
- 主要语言/框架：Qt 5.12.8（GCC 64-bit），C++17（视你的 Kit 配置）
- 组成模块：
  - 服务端（Server）：监听端口，处理来自客户端的请求
  - 客户端（Client）：向服务端发起连接与请求，并展示结果
- 实现了一个类似于腾讯会议的视频会议功能




## 2. 运行环境与依赖

必需：
- 操作系统：Linux / Windows / macOS（任选其一；下文以 Linux 为例）
- Qt 版本：Qt 5.12.8（GCC 64-bit Kit）
- 编译器与构建工具：gcc/g++、make
- 网络访问权限：本机端口监听与回环/局域网访问

可选：
- OpenSSL（若涉及 TLS/SSL）
- 其他 Qt 模块（如 QtNetwork、QtWebSockets、QtSerialPort 等）



## 3. 快速开始

### 使用 Qt Creator（推荐）

1) 打开工程
- 打开 APP 目录中的顶层工程文件（例如顶层 .pro 或 CMakeLists.txt）
- 若 client 与 server 是独立子项目，可分别打开各自的 .pro

2) 选择 Kit
- Desktop Qt 5.12.8 GCC 64bit

3) 构建与运行
- 先构建 server 子项目并运行
- 再构建 client 子项目并运行，连接到服务端

### 命令行构建（qmake 流程）

以 Linux 为例：
```bash
# 进入服务端目录，生成 Makefile 并编译
cd APP/server
mkdir -p build && cd build
qmake ..
make -j$(nproc)

# 运行服务端（示例）
./server --port 12345

# 另开终端，构建客户端
cd APP/client
mkdir -p build && cd build
qmake ..
make -j$(nproc)

# 运行客户端（示例）
./client --host 127.0.0.1 --port 12345
```

如使用 CMake，请将上述命令替换为标准 CMake 三部曲：
```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build -j
./build/<executable>
```

