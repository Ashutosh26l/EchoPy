# EchoPy (Jarvis Voice Assistant)

EchoPy is a Python-based desktop voice assistant project focused on **Windows automation** and voice-triggered actions.  
The main app listens for wake words, captures a voice command, and routes it to task handlers such as app open/close, web search, YouTube playback, dictionary lookup, Akinator mode, ad-skip automation, and a Rock-Paper-Scissors GUI game.

## Project Overview

The repository currently contains:

- **Wake-word entrypoint:** `jarvis_main.py`
- **Command router and features:** `jarvis_command.py`
- **Optional Azure TTS helper:** `speak.py`
- **Close running app helper:** `closeapp.py`
- **Rock-Paper-Scissors GUI:** `game.py`
- **Akinator mode:** `ak.py`
- **YouTube skip-ad automation scripts:** `autoskipad.py`, `skipadauto.py`
- **Packaging script (cx_Freeze):** `setup.py`

It also includes image and sound assets used by the game and assistant startup/shutdown tones.

## Key Features

- Wake word detection using Porcupine (`jarvis`, `alexa`, `ok google`)
- Speech-to-text command recognition with Google Speech Recognition
- Text-to-speech responses via `pyttsx3`
- Open and close desktop apps (Windows-focused behavior)
- Tell time
- YouTube search/play
- Google search
- Dictionary meanings/translations (`PyDictionary`)
- Wikipedia Q&A summaries
- Music playback flow with next/stop controls (expects local songs path)
- Launch Rock-Paper-Scissors game window
- Launch Akinator guessing mode
- Launch YouTube ad auto-skip mode (Selenium + ChromeDriver)

## Requirements

This project is designed around **Python on Windows** and uses several platform-specific behaviors (`taskkill`, Start menu automation, `sapi5`, `os.startfile`).

Install Python dependencies (versions are not pinned in this repo):

- pyaudio
- pvporcupine
- pydub
- SpeechRecognition
- pyttsx3
- wikipedia
- keyboard
- PyDictionary
- pywhatkit
- akinator.py
- selenium
- Pillow
- cx_Freeze
- (optional) azure-cognitiveservices-speech

## Setup Notes

1. Clone the repository and move into it.
2. Install dependencies with pip.
3. Ensure the following runtime resources exist in the project root:
   - `start up sound.wav`
   - `end up sound.wav`
   - `rock.png`, `paper.png`, `scissor.png`
   - `smallrock.png`, `smallpaper.png`, `smallscissor.png`
4. For ad-skip mode, place a compatible ChromeDriver at the path expected by the selected script (`chromedriver` or `lib/chromedriver`).
5. Update machine-specific paths in code where required (for example the music folder path in `jarvis_command.py`).

## Running

### Main Voice Assistant

Run:

```bash
python jarvis_main.py
```

Then speak a wake word (`jarvis`, `alexa`, or `ok google`) and give a command.

### Rock-Paper-Scissors Game

```bash
python game.py
```

### Akinator Mode

```bash
python ak.py
```

### Ad Skip Automation

```bash
python autoskipad.py
```

or

```bash
python skipadauto.py
```

## Example Supported Commands

- “open notepad”
- “close chrome”
- “time”
- “youtube”
- “google search”
- “dictionary”
- “question”
- “launch rock paper scissor game”
- “activate akinator mode”
- “activate automatic skip ad mode”

## Current Limitations

- Primarily Windows-only due to OS-specific APIs and command style.
- Multiple hardcoded environment assumptions exist (file paths, Chrome profile path, songs directory).
- Network-dependent features (speech recognition, Wikipedia, YouTube search) require internet access.
- `speak.py` includes direct Azure Speech configuration and is not integrated as the main speech path in command execution.

## Security and Configuration Reminder

- Do **not** commit real API keys, tokens, or personal local paths in shared/public versions.
- Replace local machine paths and credentials before production use.

## License

This repository includes a `LICENSE` file. See it for license terms.
