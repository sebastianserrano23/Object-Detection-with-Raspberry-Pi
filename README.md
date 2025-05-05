# 🎯 Real-Time Object Detection on Raspberry Pi 4 
# Final Project For CPSC 440

> A beginner-friendly project using TensorFlow Lite and Python to detect objects in real time on a Raspberry Pi 4!

Team Members: Kevin Zhuang, Sebastian Serrano, Shadan Amini

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Static Badge](https://img.shields.io/badge/Raspberry_OS-Bullseye-brown)](https://www.raspberrypi.com/software/operating-systems/)
[![Static Badge](https://img.shields.io/badge/Python-3.9.2-blue)](https://www.python.org/downloads/release/python-392/)

<div align="center">
  <img src="https://github.com/CheesyFrappe/object-detection-on-raspberry-pi/assets/80858788/e56bea78-be0f-43f3-9e1e-aa2f4efd61f0"/>
</div>

---

### 📚 Table of Contents

* [Introduction](#🧠-introduction)
* [What You Need](#what-you-need)
* [How to Use](#how-to-use)

---

## 🧠 Introduction

In this project, we used [TensorFlow Lite](https://www.tensorflow.org/lite) to build a simple object detection system that runs on a Raspberry Pi 4. It takes live video from the Pi Camera and shows boxes around objects it detects (like a mug, keyboard, etc.), with their names and confidence scores.

I used a pre-trained model called [EfficientDet-Lite0](https://www.tensorflow.org/lite/models/modify/model_maker/object_detection) which works great for real-time tasks on low-power devices like the Pi.

🕵️‍♂️ *Note: I didn’t use a Coral USB Accelerator, but the code does support it if you want faster performance. Instructions are below!*

---

## 🚀 What You Need

> \[!IMPORTANT]
> This project was tested on Raspberry Pi OS (32-bit Bullseye) with Python 3.9. The `tflite-support` library only works with Python 3.7 to 3.9.

If you're using a newer OS like Bookworm, double-check that your Python version is compatible.

> \[!TIP]
> It's recommended to use a Python virtual environment. Avoid installing packages globally with `sudo pip` as that could mess up your system tools.

### Set up your environment:

```bash
$ python3 -m venv tflite
$ source tflite/bin/activate
```

### Clone the project and install dependencies:

```bash
(tflite)$ git clone <repo-url>
(tflite)$ cd object-detection-on-raspberry-pi
(tflite)$ sh setup.sh
```

This script installs the required Python libraries and pre-trained model.

---

## 🔧 How to Use

### Default setup uses the Pi Camera

To run the project:

```bash
(tflite)$ cd src
(tflite)$ python3 detect.py
```

You should see the camera feed with boxes drawn around detected objects.

### Using a USB Webcam instead?

Open `main.py` and change the `detect()` call to:

```python
detect(False, DISPLAY_WIDTH, DISPLAY_HEIGHT, THREAD_NUM, False)
```

### Coral USB Accelerator (Optional)

Want faster detection? Plug in a Coral USB Accelerator and update the `detect()` call to:

```python
detect(False, DISPLAY_WIDTH, DISPLAY_HEIGHT, THREAD_NUM, True)
```

Then run the script again:

```bash
(tflite)$ python3 detect.py
```

Make sure you’ve followed [Google's setup guide for Coral](https://coral.withgoogle.com/docs/accelerator/get-started/).

### Troubleshooting

If you get an error like:

```bash
ImportError: ... libstdc++.so.6: version `GLIBCXX_3.4.29' not found
```

Downgrade `tflite-support`:

```bash
(tflite)$ pip install --upgrade tflite-support==0.4.3
```

---

<div align="center">
  <img src="https://github.com/CheesyFrappe/object-detection-on-raspberry-pi/assets/80858788/7278d35e-cce8-45b7-aab0-5c840ccd3dc0"/>
  <i>Example output from this project</i>
</div>

---

Now go ahead and try showing your Pi some objects like a coffee mug or keyboard, and watch the detection magic happen ✨