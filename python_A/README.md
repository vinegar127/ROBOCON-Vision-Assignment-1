# Python Project A

## 目标

持续读取摄像头，同时显示：

1. 原始画面；
2. 灰度画面；
3. 轮廓提取结果。

程序退出时保留运行期间的**未经处理的摄像头视频**。

程序启动时会打印自己的 PID、PPID、Python 可执行文件路径和 Python 版本，用于进程观察任务。

## Python 版本

```text
Python >= 3.9, < 3.11
```

推荐 Python 3.10。

## 依赖

```text
numpy >= 1.26, < 2.0
opencv-python >= 4.9, < 5.0
```

`pyproject.toml` 是版本约束的最终依据。

## 运行入口

```bash
python camera.py
```

常用参数：

```bash
python camera.py --camera 0 --output raw_capture.mp4 --width 1280 --height 720 --fps 30
```

在 OpenCV 窗口中按 `q` 或 `ESC` 退出。
