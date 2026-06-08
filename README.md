# OpenYSM

> **Yes Steve Model — Open Source Fork**
>
> 让玩家使用自定义 3D 模型替换原版 Steve/Alex 皮肤 | Replace the default Steve/Alex skin with custom 3D models

[![MC Version](https://img.shields.io/badge/Minecraft-1.20.1-blue?style=flat-square)](https://www.minecraft.net/)
[![Forge](https://img.shields.io/badge/Forge-47.4.x-orange?style=flat-square)](https://files.minecraftforge.net/)
[![Fabric](https://img.shields.io/badge/Fabric-0.16.x-yellow?style=flat-square)](https://fabricmc.net/)
[![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red?style=flat-square)](#license)

---

## 📖 项目简介 / About

**OpenYSM** 是 [Yes Steve Model](https://github.com/OpenYSMDev/OpenYSM) 的开源分支，允许玩家在 Minecraft 中使用自定义 3D 模型（基于 GeckoLib 格式）替换原版玩家皮肤。支持客户端-服务端模型同步、动画系统、多模组兼容等功能。

**OpenYSM** is an open-source fork of [Yes Steve Model](https://github.com/OpenYSMDev/OpenYSM) that allows players to replace the default Minecraft player skin with custom 3D models (GeckoLib-based format). Features client-server model synchronization, an animation system, and broad mod compatibility.

---

## 🧩 项目结构 / Project Structure

```
OpenYSM/
├── common/          # 共享代码（客户端 + 服务端通用逻辑）
│                    # Shared code (client + server common logic)
├── forge/           # Forge 平台适配层
│                    # Forge platform adapter
├── fabric/          # Fabric 平台适配层
│                    # Fabric platform adapter
└── libs/            # 第三方模组编译依赖（modCompileOnly）
                     # Third-party mod compile dependencies
```

| 模块 / Module | 平台 / Platform | MC 版本 / MC Version | 说明 / Description |
|---|---|---|---|
| `openysm-forge` | Forge 47.4.x | 1.20.1 | 客户端模组 / Client mod |
| `openysm-fabric` | Fabric 0.16.x | 1.20.1 | 客户端模组 / Client mod |
| `fox-model-loader` | Fabric | 1.21.1 | 服务端模型加载器 / Server-side model loader |

---

## ✨ 功能特性 / Features

### 🎨 自定义模型系统 / Custom Model System
- 支持 GeckoLib 格式的 3D 模型（`.ysm` 文件 / 文件夹）
- Supports GeckoLib-format 3D models (`.ysm` files / folders)
- 模型衣柜 UI：游戏内选择、预览、切换模型
- Model wardrobe UI: select, preview, and switch models in-game
- 内置默认模型：Steve、Alex、酒狐等
- Built-in default models: Steve, Alex, Wine Fox, and more

### 🔄 客户端-服务端同步 / Client-Server Sync
- 加入服务器时自动同步服务器模型到客户端
- Auto-sync server models to client on join
- 自定义加密传输协议（XChaCha20 + MT19937 + Zstd）
- Custom encrypted transfer protocol (XChaCha20 + MT19937 + Zstd)
- 客户端缓存机制，避免重复下载
- Client-side caching to avoid redundant downloads

### 🎬 动画系统 / Animation System
- 支持 GeckoLib 动画格式（`.animation.json`）
- Supports GeckoLib animation format (`.animation.json`)
- 动画控制器：基于状态机的动画切换
- Animation controllers: state-machine-based animation switching
- 内含行走、攻击、游泳、骑乘等全套动画
- Full animation set: walking, attacking, swimming, riding, etc.

### 🧩 模组兼容 / Mod Compatibility

| 模组 / Mod | 兼容状态 / Status | 说明 / Notes |
|---|---|---|
| [ParCool](https://www.curseforge.com/minecraft/mc-mods/parcool) | ✅ | 跑酷动作动画 / Parkour action animations |
| [TACZ](https://www.curseforge.com/minecraft/mc-mods/tacz) | ✅ | 枪械持握动画 / Gun holding animations |
| [SlashBlade](https://www.curseforge.com/minecraft/mc-mods/slashblade) | ✅ | 拔刀剑动画 / Slash blade animations |
| [Figura](https://www.curseforge.com/minecraft/mc-mods/figura) | ✅ | 可选替代方案 / Optional alternative |
| [Carry On](https://www.curseforge.com/minecraft/mc-mods/carry-on) | ✅ | 搬运动画 / Carry animation |
| [Create](https://www.curseforge.com/minecraft/mc-mods/create) | ✅ | 机械动画 / Mechanical animations |
| [GeckoLib](https://www.curseforge.com/minecraft/mc-mods/geckolib) | ✅ | 核心依赖 / Core dependency |
| [Curios](https://www.curseforge.com/minecraft/mc-mods/curios) | ✅ | 饰品渲染兼容 / Accessory render compat |
| [Touhou Little Maid](https://www.curseforge.com/minecraft/mc-mods/touhou-little-maid) | ✅ | 女仆模型兼容 / Maid model compat |
| [SWEM](https://www.curseforge.com/minecraft/mc-mods/swem) | ✅ | 骑马动画 / Horse riding animations |
| [Simple Planes](https://www.curseforge.com/minecraft/mc-mods/simple-planes) | ✅ | 飞行载具动画 / Aircraft animations |
| [Immersive Aircraft](https://www.curseforge.com/minecraft/mc-mods/immersive-aircraft) | ✅ | 飞行载具动画 / Aircraft animations |
| [First Person Model](https://www.curseforge.com/minecraft/mc-mods/first-person-model) | ✅ | 第一人称模型渲染 / First-person model rendering |
| [Embeddium](https://www.curseforge.com/minecraft/mc-mods/embeddium) | ✅ | 渲染优化兼容 / Render optimization compat |
| [Oculus](https://www.curseforge.com/minecraft/mc-mods/oculus) | ✅ | 光影兼容 / Shader compat |

---

## 🔧 构建指南 / Build Instructions

### 环境要求 / Prerequisites

- **JDK 17**（推荐 Alibaba Dragonwell 或 Eclipse Temurin）
- **JDK 17** (Alibaba Dragonwell or Eclipse Temurin recommended)
- **Git**

### 构建步骤 / Build Steps

```bash
# 克隆仓库 / Clone the repository
git clone https://github.com/OpenYSMDev/OpenYSM.git
cd OpenYSM

# 构建所有平台 / Build all platforms
./gradlew clean build

# 仅构建 Forge / Build Forge only
./gradlew :forge:build

# 仅构建 Fabric / Build Fabric only
./gradlew :fabric:build
```

### 输出文件 / Output Files

```
forge/build/libs/openysm-forge-2.6.5.10.jar    # Forge 版本
fabric/build/libs/openysm-fabric-2.6.5.10.jar  # Fabric 版本
```

### 关于 libs 目录 / About the libs Directory

`libs/` 目录包含第三方模组的编译时依赖 jar（`modCompileOnly`），**不会打包进最终产物**。这些 jar 需要手动下载放置。

The `libs/` directory contains third-party mod compile-time dependency jars (`modCompileOnly`), **not included in the final build output**. These jars need to be downloaded and placed manually.

---

## 🔐 安全机制 / Security Architecture

OpenYSM 采用多层加密保护模型数据传输：

OpenYSM uses multi-layer encryption to protect model data transfer:

```
传输层 / Transport Layer:
  Packet → 随机垃圾头 → XChaCha20 (30 rounds) → MT19937-XOR → CityHash64 签名

缓存层 / Cache Layer:
  Model → Zstd 压缩 (level 3) → Zstd 混淆 → 随机填充 → MT19937-XOR → XChaCha20 (10-30 rounds)

文件层 / File Layer:
  .ysm 文件 → XChaCha20 → MT19937-XOR → Zstd 解压 → 二进制反序列化
```

| 组件 / Component | 算法 / Algorithm | 说明 / Description |
|---|---|---|
| 对称加密 / Symmetric Cipher | XChaCha20 | 可变轮数（10-30），基于 CityHash 派生 / Variable rounds (10-30), CityHash-derived |
| 流密码混淆 / Stream Cipher Obfuscation | MT19937-XOR | 基于 CityHash 种子的伪随机异或 / CityHash-seeded PRNG XOR |
| 哈希验证 / Hash Verification | CityHash64 | 数据完整性签名 / Data integrity signatures |
| 压缩 / Compression | Zstd (level 3) | 自定义 block header 混淆（XOR 0xD4E9）/ Custom block header obfuscation |
| 密钥交换 / Key Exchange | ECDH (P-384) | 握手阶段密钥协商 / Handshake key agreement |

---

## 📦 模型格式 / Model Format

### 文件结构 / File Structure

```
model_folder/
├── ysm.json              # 模型元数据 / Model metadata
├── models/
│   ├── main.json          # 主模型（GeckoLib GeoModel）/ Main model (GeckoLib GeoModel)
│   └── arm.json           # 手臂模型 / Arm model
├── animations/
│   ├── main.animation.json    # 主动画 / Main animation
│   └── arm.animation.json     # 手臂动画 / Arm animation
├── textures/
│   └── skin.png           # 皮肤贴图 / Skin texture
└── lang/
    ├── en_us.json         # 英语名称 / English name
    └── zh_cn.json         # 中文名称 / Chinese name
```

### 二进制格式 / Binary Format

模型数据使用自定义二进制序列化（`YSMBinarySerializer`，format version 32），支持：
Model data uses custom binary serialization (`YSMBinarySerializer`, format version 32), supporting:

- 几何体、骨骼层级、顶点权重 / Geometry, bone hierarchy, vertex weights
- 动画关键帧、时间线事件 / Animation keyframes, timeline events
- 纹理引用、控制器逻辑 / Texture references, controller logic
- 版本化 footer（支持加密/非加密两种模式）/ Versioned footer (encrypted/unencrypted modes)

---

## 🛠️ 开发指南 / Development Guide

### 核心入口点 / Core Entry Points

| 文件 / File | 说明 / Description |
|---|---|
| `common/.../network/NetworkHandler.java` | 网络协议版本 & 通道注册 / Protocol version & channel registration |
| `common/.../model/ServerModelManager.java` | 服务端模型管理 & 同步协议 / Server model management & sync protocol |
| `common/.../client/ClientModelManager.java` | 客户端模型接收 & 缓存 / Client model reception & caching |
| `common/.../resource/YSMBinarySerializer.java` | 模型二进制序列化 / Model binary serialization |
| `common/.../resource/YSMBinaryDeserializer.java` | 模型二进制反序列化 / Model binary deserialization |
| `common/.../security/YsmCrypt.java` | 加密/解密/签名 / Encryption/decryption/signing |
| `common/.../algorithms/YsmZstd.java` | Zstd 压缩 + 混淆层 / Zstd compression + obfuscation layer |

### 协议版本 / Protocol Version

- **YSM 协议 / Protocol**: `2.6.0`
- **二进制格式 / Binary Format**: `32`
- **品牌标识 / Brand**: `open_ysm:v1`
- **加密版本 / Crypto Version**: `3` (XChaCha20 + Zstd)

---

## 📋 已知问题 / Known Issues

| 问题 / Issue | 状态 / Status | 说明 / Notes |
|---|---|---|
| WaterMedia 二进制依赖缺失 / WaterMedia binary dependency missing | ⚠️ | 视频播放功能不可用 / Video playback unavailable |
| MTS/GVP 车辆模型缺失 / MTS/GVP vehicle models missing | ⚠️ | 部分 OBJ 模型文件缺失 / Some OBJ model files missing |
| ParCool 同步偶尔超时 / ParCool sync occasional timeout | ⚠️ | 网络延迟可能导致同步失败 / Network latency may cause sync failure |

---

## 📄 许可证 / License

**All Rights Reserved.**

本项目基于 Yes Steve Model 原始代码 fork 而来。请遵循原项目的许可条款。
This project is forked from the original Yes Steve Model codebase. Please follow the original project's license terms.

---

## 🔗 相关链接 / Links

- 📦 **最新仓库 / Latest Repository**: https://github.com/OpenYSMDev/OpenYSM
- 🎮 **原版 YSM / Original YSM**: Yes Steve Model
- 📚 **GeckoLib 文档 / GeckoLib Docs**: https://github.com/bernie-g/geckolib

---

> **Note**: 本项目仅供学习和研究使用。请尊重原创作者的劳动成果。
>
> **Note**: This project is for educational and research purposes only. Please respect the original authors' work.
