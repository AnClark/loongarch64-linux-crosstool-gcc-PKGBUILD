# LoongArch64 GCC Toolchain for Arch Linux

[简体中文](https://github.com/AnClark/loongarch64-linux-crosstool-gcc-PKGBUILD#%E4%B8%BA-arch-linux-%E8%AE%BE%E8%AE%A1%E7%9A%84-loongarch64-gcc-%E5%B7%A5%E5%85%B7%E9%93%BE)

This is a `PKGBUILD` of LoongArch64 GCC Toolchain for Arch Linux, built with [Crosstool-NG](https://crosstool-ng.github.io/).

You will get a Pacman-compatible package. You can install for yourself, or install on other devices with Arch Linux (or derivatives) installed.

This project is based on a guide from _[Jiege's {maintaining, programming, and board debugging} Notes](https://jia.je/)_. Reference:

- _[Build LoongArch64 Toolchain (《LoongArch64 工具链构建》)](https://jia.je/software/2022/05/02/loongarch64-toolchain/)_

## Features

- Uses Jiege's [Crosstool-NG fork](https://github.com/jiegec/crosstool-ng/tree/loongarch) with LoongArch64 support, and [related config files](https://github.com/jiegec/ct-ng-loongarch64). But he has removed the related branch, so this repo will use [my own backup](https://github.com/anclark/crosstool-ng-loongarch64/tree/loongarch).
- No need to install Crosstool-NG into your system. Instead, directly run it within `makepkg` procedures.
- Obeys canonical path of cross-toolchains (like MinGW-w64 in Arch official repo).

## Usage

**1.** Install dependencies of Crosstool-NG:

```sh
sudo pacman -S bison flex autoconf automake help2man
```

**2.** Build:

```sh
makepkg
```

**3.** Install:

```sh
sudo pacman -U loongarch64-linux-crosstool-gcc-12.1.0-1-x86_64.pkg.tar.zst
```

## License

MIT License

---

# 为 Arch Linux 设计的 LoongArch64 GCC 工具链

这是适用于Arch Linux的LoongArch64 GCC工具链 `PKGBUILD`，借助[Crosstool-NG](https://crosstool-ng.github.io/)来构建。

最终你会得到适用于Pacman的安装包，可以为自己安装，也可以在其他Arch Linux（或衍生版本）的设备上安装并运行。

本项目基于 **[杰哥的{运维,编程,调板子}小笔记](https://jia.je/)** 的经验教程而编写，参考了他的以下文章：

- [《LoongArch64 工具链构建》](https://jia.je/software/2022/05/02/loongarch64-toolchain/)

## 功能特性

- 使用杰哥提供的[Crosstool-NG](https://github.com/jiegec/crosstool-ng/tree/loongarch)（加入了LoongArch64支持），以及相关的[配置文件](https://github.com/jiegec/ct-ng-loongarch64)。但是，原作者已经移除了相关分支，因此本repo将使用[我的备份](https://github.com/anclark/crosstool-ng-loongarch64/tree/loongarch)。
- 无需将Crosstool-NG安装到系统中，直接在`makepkg`过程中运行之。
- 遵循交叉编译工具链的安装路径规范（如Arch官方源的MinGW-w64）。

## 用法

**第一步，** 安装Crosstool-ng依赖项：

```sh
sudo pacman -S bison flex autoconf automake help2man
```

**第二步，** 开始构建：

```sh
makepkg
```

**第三步，** 安装：

```sh
sudo pacman -U loongarch64-linux-crosstool-gcc-12.1.0-1-x86_64.pkg.tar.zst
```

## 许可证

MIT License

