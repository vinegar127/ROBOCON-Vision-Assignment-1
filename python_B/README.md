# Python Project B

## 目标

读取 Project A 保存的原始视频，并进行离线处理。

输出视频包含三个并排画面：

```text
原始视频 | Canny 边缘 | 帧间运动区域
```

该项目刻意不使用 OpenCV，主要依赖 ImageIO、FFmpeg、NumPy 和 scikit-image。

## Python 版本

```text
Python >= 3.12, < 3.14
```

Project A 要求 `<3.11`，因此 A/B 必须使用两个独立环境。

## 依赖

```text
numpy >= 2.0, < 3.0
imageio >= 2.36, < 3.0
imageio-ffmpeg >= 0.5, < 1.0
scikit-image >= 0.24, < 0.27
```

`pyproject.toml` 是版本约束的最终依据。

## 运行入口

假设 Project A 的视频位于：

```text
../python_A/raw_capture.mp4
```

运行：

```bash
python analyze_video.py \
  --input ../python_A/raw_capture.mp4 \
  --output advanced_analysis.mp4
```
