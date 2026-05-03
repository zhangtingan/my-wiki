---
title: "PDF 工具箱"
date: 2026-05-03
tags:
  - PDF
  - 工具
  - 文档处理
---

# PDF 工具箱

本页面介绍 PDF 去水印工具的使用方法。

---

## 📋 功能概述

PDF 去水印工具可以去除 PDF 文件中的以下类型水印：

| 水印类型 | 说明 | 处理效果 |
|---------|------|---------|
| 文字水印 | "机密"、"样本"等重复文字 | ⭐⭐⭐⭐ |
| 图片水印 | Logo、背景图片等 | ⭐⭐⭐ |
| 背景水印 | 浅色半透明文字/图案 | ⭐⭐ |

---

## 🛠️ 使用方法

### 方式一：通过对话调用（推荐）

在 WorkBuddy 中直接说：

> "帮我去除这个 PDF 的水印"
> "PDF 去水印，文件路径是..."
> "清理 PDF 中的水印文字"

AI 会自动调用去水印工具处理。

### 方式二：命令行直接使用

```bash
python D:/workbuddy/tools/pdf_remove_watermark.py <输入.pdf> <输出.pdf> [选项]
```

#### 常用参数

| 参数 | 说明 | 示例 |
|------|------|------|
| `input.pdf` | 输入文件路径（必填） | `input.pdf` |
| `output.pdf` | 输出文件路径（必填） | `output.pdf` |
| `--mode` | 去水印模式 | `text` / `image` / `all` |
| `--pages` | 指定页码 | `1,3,5` 或 `all` |
| `--watermark-text` | 指定水印文字 | `"机密"` |

---

## 📝 使用示例

### 示例 1：去除所有页面的所有类型水印

```bash
python D:/workbuddy/tools/pdf_remove_watermark.py input.pdf output.pdf
```

### 示例 2：只去除文字水印，指定水印内容

```bash
python D:/workbuddy/tools/pdf_remove_watermark.py input.pdf output.pdf --mode text --watermark-text "机密"
```

### 示例 3：只处理指定页面

```bash
python D:/workbuddy/tools/pdf_remove_watermark.py input.pdf output.pdf --pages 1,3,5
```

### 示例 4：只去除图片水印

```bash
python D:/workbuddy/tools/pdf_remove_watermark.py input.pdf output.pdf --mode image
```

---

## ⚙️ 安装依赖

首次使用需要安装依赖：

```bash
python -m pip install PyMuPDF pillow
```

依赖说明：
- **PyMuPDF**：PDF 处理核心库
- **Pillow**：图像处理辅助库

---

## 💡 使用技巧

### 1. 先测试后批量

```bash
# 先测试第 1 页效果
python pdf_remove_watermark.py input.pdf test.pdf --pages 1

# 效果满意后处理全部
python pdf_remove_watermark.py input.pdf output.pdf
```

### 2. 指定水印文字提高准确率

```bash
# 不指定：自动检测（可能误删）
# 指定后：精确删除
python pdf_remove_watermark.py input.pdf output.pdf --mode text --watermark-text "公司内部资料"
```

### 3. 保留原文件

```bash
# 原文件：document.pdf
# 输出文件：document_clean.pdf
python pdf_remove_watermark.py document.pdf document_clean.pdf
```

---

## ⚠️ 注意事项

1. **备份原文件** - 处理前请备份原始 PDF
2. **效果因文件而异** - 复杂水印可能无法完全去除
3. **加密 PDF** - 需要先解密才能处理
4. **输出文件** - 会自动覆盖同名文件

---

## 🔧 故障排除

### 问题 1：提示"ModuleNotFoundError: No module named 'fitz'"

**解决方法**：安装 PyMuPDF
```bash
python -m pip install PyMuPDF
```

### 问题 2：去水印效果不理想

**可能原因**：
- 水印类型识别不准确 → 尝试指定 `--mode` 参数
- 文字水印内容不匹配 → 使用 `--watermark-text` 指定准确文字
- 水印与正文合并 → 无法完全分离，建议手动编辑

### 问题 3：处理后的文件变大

**原因**：PyMuPDF 重新生成 PDF 时可能不压缩图片
**解决**：使用 PDF 压缩工具进一步处理

---

## 📚 相关资源

- [PyMuPDF 官方文档](https://pymupdf.readthedocs.io/)
- [Pillow 官方文档](https://pillow.readthedocs.io/)
- [PDF 格式详解](https://en.wikipedia.org/wiki/PDF)

---

## 📊 处理效果对比

```
┌─────────────────────────────────────────┐
│         处理效果对比示例               │
├─────────────┬───────────┬───────────┤
│  原文件     │  处理后    │  效果评分  │
├─────────────┼───────────┼───────────┤
│  文字水印   │  文字消失  │  ⭐⭐⭐⭐⭐ │
│  图片水印   │  图片移除  │  ⭐⭐⭐⭐   │
│  背景水印   │  明显淡化  │  ⭐⭐⭐     │
└─────────────┴───────────┴───────────┘
```

---

*持续更新中，欢迎反馈使用体验！*
