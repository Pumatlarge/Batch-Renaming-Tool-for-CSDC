# 📄 PDF Batch Renaming Tool for CSDC-PDF

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)

🌍 Language / 语言： [🇨🇳 中文说明](#中文说明) \| [🇺🇸 English](#english)

------------------------------------------------------------------------

## 🚀 Project Overview

A local offline PDF batch renaming tool designed for securities document
processing.

Automatically extracts: - Sub-account number - Holder name

Generates standardized filenames while preserving original files.

------------------------------------------------------------------------

# 中文说明

## 📌 项目简介

本工具用于批量处理中国证券登记结算系统导出的 PDF 文件。

自动提取：

-   证券子账户号码
-   持有人名称

并生成"证券账户号码-人名" 标准格式文件名。

------------------------------------------------------------------------

## ✨ 功能特点

-   ✅ 支持拖拽单个 / 多个 PDF
-   ✅ 支持拖拽文件夹
-   ✅ 自动创建输出子文件夹
-   ✅ 自动防止重名
-   ✅ 保留原文件
-   ✅ 自动生成日志文件
-   ✅ 完全离线运行

------------------------------------------------------------------------

## 📂 命名规则

    新文件名 = 证券子账户号码-持有人名称.pdf

------------------------------------------------------------------------

## 📁 输出目录结构

    某目录
    ├── 原PDF文件
    ├── 已重命名输出
    │   ├── A2900849561-陈小美.pdf
    │   ├── 重命名日志.csv

------------------------------------------------------------------------

## 🛠 安装方式

### 方式一：直接下载 EXE（推荐）

在 Releases 页面下载：

    PDF重命名工具v0.2-中登投资者证券持有变更信息.exe

------------------------------------------------------------------------

### 方式二：源码运行

``` bash
pip install pdfplumber
python rename_pdf_drag.py
```

------------------------------------------------------------------------

## 🔒 安全说明

-   本工具完全本地运行
-   不联网
-   不上传数据
-   适用于证券类敏感文件内网处理

------------------------------------------------------------------------

## 📜 License

This project is licensed under the MIT License.

------------------------------------------------------------------------

# English

## 📌 Overview

This tool is designed for batch processing PDF files exported from
securities systems.

It automatically extracts:

-   Sub-account number
-   Holder name

and generates standardized filenames.

------------------------------------------------------------------------

## ✨ Features

-   ✅ Drag & Drop support
-   ✅ Folder support
-   ✅ Duplicate prevention
-   ✅ Log file generation
-   ✅ Original files preserved
-   ✅ Fully offline

------------------------------------------------------------------------

## 📂 Naming Rule

    SubAccountNumber-HolderName.pdf

------------------------------------------------------------------------

## 🛠 Installation

### Option 1: Download EXE (Recommended)

Download from the Releases page:

    PDF重命名工具v0.2-中登投资者证券持有变更信息.exe

------------------------------------------------------------------------

### Option 2: Run from Source

``` bash
pip install pdfplumber
python rename_pdf_drag.py
```

------------------------------------------------------------------------

## 🔒 Security Notice

-   Fully offline
-   No data upload
-   Safe for internal securities documents
