    /^\    /^\
    {  O}  {  O}
     \ /    \ /
     //     //       _------_
    //     //     ./~        ~-_
   / ~----~/     /              \
 /         :   ./       _---_    ~-
|  \________) :       /~     ~\   |
|        /    |      |  :~~\  |   |
|       |     |      |  \___-~    |
|        \ __/`^\______\.        ./
 \                     ~-______-~\.
 .|                                ~-_
/_____________________________________~~__

# Universal Media Downloader (Portable USB)

A cross-platform, self-contained media downloader designed to live and run directly from a portable USB drive on both **Windows** and **Linux**. 

Powered by `yt-dlp`, `spotdl`, `FFmpeg`, and `CustomTkinter`, it provides a modern dark-mode GUI for downloading videos, audio tracks, and full playlists without requiring pre-installed dependencies on target machines once built.

---

## Features

- **Multi-Platform Support:** Supports YouTube, TikTok, Instagram, SoundCloud, Twitter/X, and hundreds of other sites via `yt-dlp`.
- **Spotify Playlist & Track Support:** Automatically detects Spotify links and downloads tracks/playlists via `spotdl` without requiring personal Spotify Developer API keys.
- **Flexible Format & Quality Controls:**
  - **Video Formats:** `MP4`, `MKV`, `WEBM`, `MOV`, `AVI` (High, Medium 720p, and Low quality presets).
  - **Audio Formats:** `MP3`, `OGG` (Vorbis), `OPUS`, `FLAC` (Lossless), `M4A`, `WAV` (320kbps, 192kbps, and 128kbps bitrates).
- **Playlist & Folder Organization:** Automatically organizes playlists into named subfolders with track numbering, while placing individual files in a dedicated `Standalone Downloads` folder.
- **Self-Healing Platform Manager:** Includes `Universal_Manager.py`, which detects your OS, verifies the health of the compiled executable, automatically rebuilds the app if any files are missing or broken, and opens the launcher.
- **100% Portable Execution:** Bundles Python, all libraries, and `FFmpeg`/`FFprobe` binaries into standalone directories (`Windows/` and `Linux/`) with automatic `noexec` USB mount workarounds on Linux.

---

## Project Structure

```text
MediaDownloader_Portable/
├── Start_Universal.bat        # Windows double-click entry point
├── Start_Universal.sh         # Linux entry point
├── .gitignore                 # Excludes local builds, venv, and downloads
├── README.md                  # Project documentation
├── Downloads/                 # Auto-created folder where saved media is stored
├── Windows/                   # Auto-generated portable Windows build (ignored by Git)
├── Linux/                     # Auto-generated portable Linux build (ignored by Git)
└── Source/
    ├── Universal_Manager.py   # Platform selector, health checker & auto-rebuilder GUI
    ├── launcher.py            # Portable launcher & build status manager
    ├── setup_app.py           # Automated dependency installer & PyInstaller builder
    ├── downloader.py          # Main CustomTkinter downloader application
    └── requirements.txt       # Python package dependencies
```

---

## Prerequisites (Build Machine Only)

You only need Python installed on the machine where you initially build the portable binaries. Once built, the generated `Windows/` and `Linux/` folders can run on any compatible machine without Python installed.

- **Python 3.10+** (with `tkinter` enabled)
- **Internet connection** (for downloading packages and FFmpeg during initial setup)

---

## How to Run & Build

### Windows

1. Navigate to the `MediaDownloader_Portable` folder.
2. Double-click **`Start_Universal.bat`**.
3. In the **Platform Manager** window, click **Windows (Current)**.
   - On first run, the manager will detect that the Windows build does not exist yet and will automatically install dependencies, bundle `FFmpeg`, and compile `Windows/downloader/downloader.exe`.
4. Once complete, the **Launcher** will open automatically. Click **Launch Downloader** to start downloading.

### Linux

1. Open a terminal in the `MediaDownloader_Portable` folder and make the startup script executable (first time only):
   ```bash
   chmod +x Start_Universal.sh
   ```
2. Run the script (or double-click it in your file manager and choose *Run as Program*):
   ```bash
   ./Start_Universal.sh
   ```
3. In the **Platform Manager** window, click **Linux (Current)**.
   - On first run, `setup_app.py` will verify `ffmpeg`, `python3-tk`, and `libpython` (installing them via `apt`, `dnf`, or `pacman` if needed), create an isolated virtual environment, and compile the portable Linux binary.
4. Once finished, click **Launch Downloader** in the Launcher window.

---

## Updating & Rebuilding

If you modify `Source/downloader.py`:

1. Open `Start_Universal.bat` (Windows) or `Start_Universal.sh` (Linux).
2. Check **"Force clean rebuild before opening Launcher"**.
3. Click your current operating system (**Windows** or **Linux**). The manager will wipe stale build caches, recompile the executable, and open the Launcher automatically.

> **Note on Cross-OS Builds:** PyInstaller builds native binaries for the operating system it runs on. To prepare a single USB drive that works on both OSes, run the setup once on a Windows PC (to populate `Windows/`) and once on a Linux PC (to populate `Linux/`).

---

## Disclaimer

This tool is intended for personal, educational, and archival use only. Please respect copyright laws and the Terms of Service of the platforms you download content from.

