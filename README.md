# DnD Ambience Player

A tiny desktop app for D&D (or any tabletop) sessions: a window full of buttons, one per scene, that instantly plays the matching background track. No playlists to manage mid-session, no alt-tabbing to a music app — click the scene, the mood changes.

## Features

- One-click playback per scene (tavern, battle, temple, etc.)
- Switching tracks stops whatever's playing and starts the new one — no overlap
- A "Stop Music" button to cut audio entirely
- If a track is ever missing, a file picker pops up so you can locate it manually instead of the app just failing silently
- Ships with its own audio files in [`musics/`](musics/) — clone and run, nothing to configure

## How it works

The app is a single [Jupyter notebook](the_program.ipynb) containing a small Python script:

- **tkinter** builds the window and one button per ambience track
- **pygame.mixer** handles actual audio playback
- Each button is mapped to an mp3 file in the [`musics/`](musics/) folder next to the notebook; clicking it loads and plays that file, replacing whatever was playing before

Current scenes: Opening battle, Tavern, The Journey Begins, Zombie Attack, Kobold Ambush, Temple, Runara (first appearance / transformation), Courage in the Storm.

## Setup

Requires Python 3 and [Jupyter](https://jupyter.org/install).

```bash
git clone https://github.com/yusufkrtp/ambient_music_player.git
cd ambient_music_player
pip install -r requirements.txt
```

## Running it

Open and run [`the_program.ipynb`](the_program.ipynb) (e.g. `jupyter notebook the_program.ipynb`, then Run All). A window with one button per track will appear — click a button to play that scene's music, click **Stop Music** to stop.

## Adding your own tracks

Drop an mp3 into [`musics/`](musics/) and add an entry to the `AMBIENCE_FILES` dictionary in the notebook, mapping a button label to the filename. A button for it appears automatically the next time you run the notebook.
