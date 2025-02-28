# Video Translation with Voice Cloning

A Python script that translates the audio of an English video into any language using AI, clones the original speaker's voice with open-source software, and generates a new video with the translated audio.

## Features

- Extracts audio from video files (e.g., MP4, AVI).
- Transcribes English audio to text with timestamps.
- Translates text into a target language using AI models.
- Clones the original speaker's voice for natural-sounding audio in the target language.
- Replaces the original audio with the translated version in the video.

## Requirements

- **Python 3.7+**
- **Dependencies:**
  - `moviepy`: Video and audio processing
  - `vosk`: Offline speech-to-text
  - `transformers`: AI translation
  - `pydub`: Audio manipulation
- **Voice Cloning Tool:** An open-source solution like [XTTS by Coqui AI](https://github.com/coqui-ai/TTS) (or substitute with your preferred tool).

## Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/lexciobotariu/polyVideo.git
   cd polyVideo
   ```

2. **Install Python Dependencies:**
   ```bash
   pip install moviepy vosk transformers pydub
   ```

3. **Set Up Vosk Model:**
   - Download a Vosk model (e.g., `vosk-model-en-us-0.22`) from [Vosk Models](https://alphacephei.com/vosk/models).
   - Extract it to a directory (e.g., `./vosk-model`).

4. **Install Voice Cloning Software:**
   - Example using XTTS:
     ```bash
     git clone https://github.com/coqui-ai/TTS
     cd TTS
     pip install -e .
     ```
   - Refer to the tool’s documentation for additional setup (e.g., pre-trained models).

## Usage

Run the script with the following command:

```bash
python translate_video.py --video path/to/video.mp4 --target_lang fr --voice_sample 00:01:00-00:01:30 --output path/to/output.mp4
```

### Arguments
| Argument         | Description                                      | Required | Default                |
|------------------|--------------------------------------------------|----------|------------------------|
| `--video`        | Path to the input video file                    | Yes      | N/A                    |
| `--target_lang`  | Target language code (e.g., `fr` for French)    | Yes      | N/A                    |
| `--voice_sample` | Time range for voice sample (e.g., `mm:ss-mm:ss`) | No       | First 30 seconds       |
| `--output`       | Path to save the translated video               | Yes      | N/A                    |

## Example

Translate a video from English to Spanish:

```bash
python translate_video.py --video demo.mp4 --target_lang es --output demo_es.mp4
```

This creates `demo_es.mp4` with Spanish audio in the original speaker’s cloned voice.

## How It Works

1. Extracts audio from the video using `moviepy`.
2. Captures a voice sample for cloning (default or user-specified).
3. Transcribes audio to text with timestamps using `vosk`.
4. Translates text to the target language with `transformers`.
5. Generates translated audio with a cloned voice using the chosen voice cloning tool.
6. Assembles the new audio track with `pydub`.
7. Combines the new audio with the original video using `moviepy`.

## Limitations

- Audio timing may not perfectly sync with the video due to language length differences.
- Voice cloning quality depends on the sample provided and the chosen tool.
- Currently supports English as the source language only.

## Contributing

Contributions are welcome! Please:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-name`).
5. Open a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- [Vosk](https://alphacephei.com/vosk/) for speech recognition.
- [Hugging Face Transformers](https://huggingface.co/docs/transformers) for translation.
- [Coqui AI TTS](https://github.com/coqui-ai/TTS) (or your chosen voice cloning tool) for voice synthesis.
