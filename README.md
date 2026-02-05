# srt_file_generator
Struggling to find the right .SRT files for Non English movies or want to generate .SRT files with English meaning for your native content, then this srt_file_generator might be for you. I experimented with 'Telugu' my native language. 

# 🎥 Telugu Video to English Subtitles Generator (Advanced)

An advanced Python tool leveraging OpenAI's state-of-the-art **Whisper Large-v3** model to transcribe Telugu audio and generate high-accuracy English subtitles (`.srt`).

Unlike basic implementations, this tool uses **Context Prompting** and **Beam Search** to solve common "hallucination" issues, ensuring accurate context even for complex Telugu sentences.

## 🚀 Features

- **Model Accuracy**: Uses `large-v3` (OpenAI's best model) for superior Telugu understanding compared to standard `medium` or `base` models.
- **Context-Aware**: Includes a `prompt_context` parameter to "hint" the AI about the video topic (e.g., "Cooking," "Tech Vlog"), drastically reducing mistranslations.
- **Enhanced Decoding**: Implements `beam_size=5` to evaluate multiple translation paths for the most grammatically correct output.
- **GPU Optimized**: Automatically detects CUDA (NVIDIA GPU) for 5x-10x faster processing using FP16 precision.
- **CapCut Ready**: Outputs standard `.srt` files fully compatible with CapCut, Premiere Pro, and DaVinci Resolve.

## 🛠️ Prerequisites

1.  **Python 3.8+**
2.  **FFmpeg** (Required for audio processing)
    - *Windows (PowerShell Admin):* `winget install Gyan.FFmpeg`
    - *Mac (Homebrew):* `brew install ffmpeg`
3.  **NVIDIA GPU (Recommended)**: The `large-v3` model requires ~10GB VRAM for optimal speed. (CPU mode works but is slower).

## 📦 Installation

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/SuryaKumarIndurthy/srt_file_generator.git
   
    cd srt_file_generator
    ```

2.  **Install Dependencies**:
    ```bash
    pip install openai-whisper torch notebook
    ```

## 💻 Usage

1.  **Launch Jupyter Notebook**:
    ```bash
    jupyter notebook
    ```

2.  **Configure & Run**:
    - Open `subtitle_generator.ipynb`.
    - Place your video (e.g., `vlog.mp4`) in the folder.
    - **Crucial Step**: Update the `context_hint` in the last cell to match your video topic:
      ```python
      # Example for a food vlog
      context_hint = "A Telugu video about cooking Hyderabadi Biryani and street food."
      ```
    - Run all cells.

3.  **Output**:
    - A time-synced file named `vlog.srt` will be generated.

## ⚙️ Advanced Configuration

You can tweak the `generate_srt_advanced` parameters in the code:

| Parameter | Default | Description |
| :--- | :--- | :--- |
| `model_size` | `large-v3` | Best accuracy. Switch to `medium` if you run out of GPU memory. |
| `beam_size` | `5` | Checks 5 alternative translations per sentence. Higher = better quality but slower. |
| `temperature` | `0` | Set to 0 to force factual accuracy. Increase (0.2) for more creative translations. |

## 🎬 Importing into CapCut

1.  Open **CapCut Desktop**.
2.  Go to **Text** > **Local Captions**.
3.  **Import** the generated `.srt` file.
4.  *Tip*: Select all caption clips and apply a "Yellow" font style for better visibility.

## 🤝 Troubleshooting

- **Error: `CUDA out of memory`**
  - *Fix:* Your GPU VRAM is full. Switch `model_size` from `large-v3` to `medium` in the code.
  
- **Issue: Subtitles are still slightly off?**
  - *Fix:* Make your `context_hint` more specific. Instead of just "Vlog," try "A Telugu travel vlog visiting the Charminar in Hyderabad."

## 📄 License

This project is open-source and available under the MIT License.
