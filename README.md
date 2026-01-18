# 📄🎵🎬 PDF-Audio-video2Markdown

> 🤖 **Universal AI Skill** for Claude Code / Cursor / Antigravity / Windsurf and more

[![Claude Code](https://img.shields.io/badge/Claude_Code-Compatible-8A2BE2?logo=anthropic&logoColor=white)](https://claude.ai)
[![Cursor](https://img.shields.io/badge/Cursor-Compatible-00DC82?logo=cursor&logoColor=white)](https://cursor.com)
[![Antigravity](https://img.shields.io/badge/Antigravity-Compatible-FF6B6B)](https://antigravity.dev)
[![Windsurf](https://img.shields.io/badge/Windsurf-Compatible-0EA5E9)](https://windsurf.ai)

[![Python 3.10-3.12](https://img.shields.io/badge/Python-3.10--3.12-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/evan966890/PDF-Audio-video2Markdown?style=social)](https://github.com/evan966890/PDF-Audio-video2Markdown)
[![GitHub forks](https://img.shields.io/github/forks/evan966890/PDF-Audio-video2Markdown?style=social)](https://github.com/evan966890/PDF-Audio-video2Markdown)

---

**🇨🇳 中文** | **🇺🇸 English below**

将 PDF / 音频 / 视频 / 图像 **智能转换**为 Markdown 文本，特别适合**会议录屏转文字**场景。

Intelligently convert PDF, Audio, Video & Images to Markdown text, especially optimized for **meeting recordings transcription**.

---

## 📋 Table of Contents

- [Why This Tool](#-why-this-tool)
- [Features](#-features)
- [Quick Start](#-quick-start)
- [IDE Integration](#-ide-integration)
- [Usage](#-usage)
- [Supported Formats](#-supported-formats)
- [Architecture](#-architecture)
- [FAQ](#-faq)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [Acknowledgments](#-acknowledgments)

---

## 🎯 Why This Tool

| Pain Point 痛点 | Solution 解决方案 |
|----------------|------------------|
| 会议录屏无法搜索、回顾耗时 | 自动转写为可搜索的 Markdown |
| 扫描版 PDF 无法复制文字 | 智能 OCR 自动识别 |
| 音视频文件太大导致内存溢出 | 自动分段处理，30秒一段 |
| 环境配置复杂、依赖难装 | 一键自动安装，内置重试机制 |
| 不同 IDE 需要不同配置 | 通用 Skill 格式，一次编写到处使用 |

---

## ✨ Features

| Feature | 功能 | Description |
|---------|------|-------------|
| 🔄 **Multi-format** | 多格式支持 | PDF, Audio (MP3/WAV/M4A), Video (MP4/AVI/MKV), Images (PNG/JPG) |
| 🧠 **Smart OCR** | 智能OCR | Auto-detect scanned vs text PDF, process accordingly |
| 🎬 **Meeting Ready** | 会议优化 | Optimized for meeting recordings and screen captures |
| 📦 **Chunked Processing** | 分段处理 | Auto-chunk large files to prevent OOM |
| 🔁 **Auto Retry** | 自动重试 | Built-in retry mechanism (3x per file, 10x for E2E) |
| 🔒 **Fully Offline** | 完全离线 | All processing done locally, privacy protected |
| ⚡ **Zero Config** | 零配置 | Auto-install dependencies, works out of the box |
| 🌍 **Portable** | 可移植 | Copy to any machine, no absolute paths |

---

## 🚀 Quick Start

### 3 Steps to Get Started

```bash
# 1. Clone 克隆
git clone https://github.com/evan966890/PDF-Audio-video2Markdown.git
cd PDF-Audio-video2Markdown

# 2. Setup 配置环境
python scripts/setup_environment.py

# 3. Test 测试
python scripts/run_e2e_test.py
```

That's it! 就这么简单！

---

## 🔧 IDE Integration

This skill works with **any AI-powered IDE** that supports the skill format:

### Claude Code

```bash
# Copy to user skills directory
cp -r PDF-Audio-video2Markdown ~/.claude/skills/

# Or project-level
cp -r PDF-Audio-video2Markdown .claude/skills/
```

### Cursor

```bash
# Copy to user skills directory
cp -r PDF-Audio-video2Markdown ~/.cursor/skills/

# Or project-level
cp -r PDF-Audio-video2Markdown .cursor/skills/
```

### Antigravity

```bash
cp -r PDF-Audio-video2Markdown ~/.antigravity/skills/
```

### Windsurf

```bash
cp -r PDF-Audio-video2Markdown ~/.windsurf/skills/
```

### Other IDEs

Copy to the IDE's skill directory. The skill follows the standard `SKILL.md` format.

---

## 📖 Usage

### Process Single File | 处理单个文件

```bash
python scripts/process_file.py <file_path> [output_dir]

# Examples 示例
python scripts/process_file.py ./input/meeting.mp4
python scripts/process_file.py ./input/report.pdf ./output
python scripts/process_file.py ./input/screenshot.png
```

### Batch Processing | 批量处理

```bash
python scripts/process_all.py [input_dir] [output_dir]

# Example 示例
python scripts/process_all.py ./input ./output
```

### End-to-End Test | 端到端测试

```bash
python scripts/run_e2e_test.py
```

Interactive test that:
- Auto-configures environment
- Asks for test directory
- Retries until success (max 10 times)

---

## 📁 Supported Formats

| Type 类型 | Formats 格式 | Use Case 适用场景 |
|----------|-------------|------------------|
| 🎬 Video | MP4, AVI, MKV, MOV | Meeting recordings, tutorials |
| 🎵 Audio | MP3, WAV, M4A, FLAC | Voice memos, interviews |
| 📄 PDF | PDF (text/scanned) | Documents, reports, books |
| 🖼️ Image | PNG, JPG, JPEG, TIFF | Screenshots, scanned pages |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Input File 输入文件                        │
└─────────────────────────┬───────────────────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│               File Type Detection 文件类型检测                │
└─────────────────────────┬───────────────────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                Smart Router 智能路由                          │
├──────────────┬──────────────┬──────────────┬────────────────┤
│   PDF 路由   │  Audio 路由  │  Video 路由  │   Image 路由   │
├──────┬───────┼──────┬───────┼──────────────┼────────────────┤
│Text层│Scanned│Small │ Large │Extract Audio │     OCR        │
│      │       │      │Chunked│              │                │
├──────┴───────┼──────┴───────┼──────────────┼────────────────┤
│   PyMuPDF    │    FunASR    │    pydub     │   RapidOCR     │
│   RapidOCR   │              │   FunASR     │                │
└──────────────┴──────────────┴──────────────┴────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────────┐
│              Markdown Output 输出 Markdown                   │
└─────────────────────────────────────────────────────────────┘
```

### Processing Strategies | 处理策略

| Scenario 场景 | Strategy 策略 | Speed 速度 |
|--------------|---------------|-----------|
| PDF with text layer | Direct extract 直接提取 | ~0.1s/page |
| Scanned PDF | OCR per page | ~2s/page |
| Audio ≤10MB | Direct transcribe | Fast |
| Audio >10MB | 30s chunked | Stable |
| Video | Extract audio → Transcribe | Depends on length |

---

## ❓ FAQ

<details>
<summary><b>Python version error / Python 版本错误</b></summary>

```
[FAIL] Python 3.13 版本过高
```

**Solution**: Install Python 3.10-3.12, or use `py -3.12` to specify version.

</details>

<details>
<summary><b>Chinese garbled text on Windows / Windows 中文乱码</b></summary>

```powershell
$env:PYTHONIOENCODING='utf-8'
python scripts/process_file.py ...
```

</details>

<details>
<summary><b>Out of memory / 内存不足</b></summary>

Large files are auto-chunked. If still failing, edit `scripts/process_file.py`:

```python
AUDIO_CHUNK_DURATION_SEC = 15  # Reduce chunk size
```

</details>

<details>
<summary><b>FFmpeg not found</b></summary>

Install FFmpeg:
- **Windows**: `winget install FFmpeg` or download from [ffmpeg.org](https://ffmpeg.org)
- **macOS**: `brew install ffmpeg`
- **Linux**: `sudo apt install ffmpeg`

</details>

More FAQ: See `references/troubleshooting.md`

---

## 🗺️ Roadmap

- [x] PDF text extraction & OCR
- [x] Audio/Video transcription (FunASR)
- [x] Smart routing & chunked processing
- [x] Auto environment setup
- [x] Multi-IDE support (Claude Code, Cursor, etc.)
- [ ] Speaker diarization (who said what)
- [ ] Timestamp alignment
- [ ] Table extraction from PDF
- [ ] GPU acceleration support
- [ ] Web UI interface
- [ ] Docker container

**Have ideas?** [Open an issue](https://github.com/evan966890/PDF-Audio-video2Markdown/issues)!

---

## 🤝 Contributing

We welcome contributions! 欢迎贡献！

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Quick Contribution Guide

1. Fork the repo
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push: `git push origin feature/amazing-feature`
5. Open a Pull Request

### Contributors

<!-- readme: contributors -start -->
<!-- readme: contributors -end -->

---

## 📜 License

MIT License - see [LICENSE](LICENSE)

---

## 🙏 Acknowledgments

| Project | Usage |
|---------|-------|
| [PyMuPDF](https://github.com/pymupdf/PyMuPDF) | PDF text extraction |
| [RapidOCR](https://github.com/RapidAI/RapidOCR) | OCR engine (ONNX) |
| [FunASR](https://github.com/alibaba-damo-academy/FunASR) | Speech recognition |
| [pydub](https://github.com/jiaaro/pydub) | Audio processing |

---

<p align="center">
  <b>⭐ Star this repo if you find it useful! ⭐</b>
  <br>
  <b>如果觉得有用，请点个 Star！</b>
</p>
