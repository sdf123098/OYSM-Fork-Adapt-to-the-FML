# Changelog / 更新日志

All notable changes to OpenYSM will be documented in this file.
OpenYSM 的所有重要变更将记录在此文件中。

---

## [2.6.5.10] — 2026-06-08

> 本版本主要修复了客户端与服务端之间的 YSM 模型同步失败问题。
>
> This release primarily fixes YSM model synchronization failure between client and server.

### 🐛 Bug Fixes / 修复

- **Fix Zstd decompression failure when syncing models from server** — 修复从服务器同步模型时 Zstd 解压失败的问题

  - **Root cause / 根因**: The client's `YsmZstd.decompress()` always called `washInPlace` with `preserveChecksumFlag=false` (unconditionally clearing the ZSTD frame checksum flag bit), while the server's newer implementation uses a try-strict-then-fallback pattern with `preserveChecksumFlag=true`. This caused the ZSTD block header deobfuscation to produce misaligned data, resulting in `MalformedInputException: Invalid magic prefix` for every model downloaded from the server.

  - **Root cause / 根因**: 客户端的 `YsmZstd.decompress()` 始终以 `preserveChecksumFlag=false` 调用 `washInPlace`（无条件清除 ZSTD 帧校验和标志位），而服务端新版本使用了先 strict 后 fallback 的模式，`preserveChecksumFlag=true`。这导致 ZSTD block header 解混淆后数据偏移错位，从服务器下载的每个模型都抛出 `MalformedInputException: Invalid magic prefix`。

  - **Changes / 变更**:
    - `YsmZstd.java`: Added `decompressStrict()` method, `copyInput()` helper, and `washInPlace()` overload with `preserveChecksumFlag` parameter. Updated `decompress()` to try strict decompression first, falling back to legacy mode on failure — matching the server-side Fox-Model-Loader implementation.
    - `YsmZstd.java`: 新增 `decompressStrict()` 方法、`copyInput()` 辅助方法、带 `preserveChecksumFlag` 参数的 `washInPlace()` 重载。更新 `decompress()` 为先尝试 strict 解压、失败后 fallback 到 legacy 模式——与服务端 Fox-Model-Loader 实现保持一致。

- **Fix SlashBlade dependency classpath conflict** — 修复 SlashBlade 依赖类路径冲突

  - **Root cause / 根因**: Both `x_SlashBlade-1.20.1-0.1.2.jar` (old API) and `SlashBladeResharped-1.20.1-0.1.4-patched.jar` (new API) were on the compile classpath. The compiler resolved `ISlashBladeState.getComboSeq()` from the old jar (returning `ComboState`), causing a type mismatch with the code expecting `ResourceLocation` from the new API.

  - **Root cause / 根因**: `x_SlashBlade-1.20.1-0.1.2.jar`（旧 API）和 `SlashBladeResharped-1.20.1-0.1.4-patched.jar`（新 API）同时存在于编译类路径。编译器从旧 jar 解析 `ISlashBladeState.getComboSeq()`（返回 `ComboState`），与代码期望的新 API 返回类型 `ResourceLocation` 产生类型不匹配。

  - **Changes / 变更**:
    - `forge/build.gradle`: Swapped dependency order — `x_SlashBlade` now listed before `SlashBladeResharped` so the newer API classes take classpath precedence.
    - `forge/build.gradle`: 交换依赖顺序——`x_SlashBlade` 移至 `SlashBladeResharped` 之前，使新 API 类优先加载。

### 📝 Documentation / 文档

- **Added bilingual README** — 新增中英双语 README
  - Project overview, build instructions, security architecture, model format, mod compatibility table, development guide.
  - 项目概览、构建指南、安全架构、模型格式、模组兼容表、开发指南。

---

## [2.6.5.9] — Previous Release / 之前版本

- Initial OpenYSM fork from Yes Steve Model.
- OpenYSM 从 Yes Steve Model 初始 fork。
