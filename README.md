# srt_file_generator
Struggling to find the right .SRT files for Non English movies or want to generate .SRT files with English meaning for your native content, then this srt_file_generator might be for you. I experimented with 'Telugu' my native language.

# 🎥 Telugu Video to English Subtitles Generator

A Python tool that leverages OpenAI's Whisper model to automatically transcribe Telugu audio from video files and generate time synced English subtitles (`.srt`). 

Designed to streamline the workflow for editing Telugu content in CapCut, Premiere Pro, or DaVinci Resolve, addressing the lack of native Telugu support in most auto captioning tools.

## 🚀 Features

 Direct Translation: Converts Telugu audio directly to English text (skipping the Telugu transcription step for better context).
 Format Support: Supports MP4, MKV, MOV, and AVI inputs.
 CapCut Ready: Generates standard `.srt` files compatible with CapCut's "Local Captions" import.
 GPU Acceleration: Automatically detects CUDA (NVIDIA GPU) to speed up transcoding by 5x10x.
 Customizable Accuracy: Switch between `base`, `medium`, or `large` Whisper models depending on your hardware.

## 🛠️ Prerequisites

Before running the notebook, ensure you have the following installed:

1.  Python 3.8+
2.  FFmpeg (Required for audio processing)
     Windows (PowerShell Admin): `winget install Gyan.FFmpeg`
     Mac (Homebrew): `brew install ffmpeg`
3.  NVIDIA Drivers (Optional, but recommended for GPU acceleration)

## 📦 Installation

1. Install Python Dependencies:
    ```bash
    pip install openaiwhisper torch notebook
    ```

## 💻 Usage

1.  Launch Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

2.  Run the Generator:
     Place your video file (e.g., `vlog_footage.mp4`) in the same folder.
     Update the filename variable in the last cell:
      ```python
      video_filename = "my_telugu_video.mp4"
      ```
     Run all cells.

3.  Output:
     The tool will generate a file named `my_telugu_video.srt` in the same directory.

## 🎬 Importing into CapCut

1.  Open your project in CapCut Desktop.
2.  Navigate to Text (top menu) > Local Captions (left sidebar).
3.  Click Import and select the generated `.srt` file.
4.  The English meanings will appear on the timeline, perfectly synced with your Telugu audio.

## ⚙️ Configuration

You can adjust the `model_size` in the code to balance speed vs. accuracy:

| Model Size | Speed | Accuracy | VRAM Required |
| : | : | : | : |
| `base` | Very Fast | Low | ~1 GB |
| `small` | Fast | Moderate | ~2 GB |
| `medium` | Moderate | High (Recommended) | ~5 GB |
| `large` | Slow | Very High | ~10 GB |

## 🤝 Troubleshooting

 Error: `FileNotFoundError: [WinError 2] The system cannot find the file specified`
   Fix: This means FFmpeg is not installed or not in your system PATH. Run `winget install Gyan.FFmpeg` and restart your computer.

 Warning: `FP16 is not supported on CPU; using FP32 instead`
   Fix: This is normal if you don't have a GPU. The code will still run, just slower.

## 📄 License

This project is opensource and available under the MIT License.
