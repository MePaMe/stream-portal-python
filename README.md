# Stream Portal GUI

A Python desktop application for IPTV/portal style streaming with:
- MAC-based channel filtering
- M3U import support
- JSON channel configuration
- HLS / RTMP / HTTP stream support
- Desktop GUI built with Tkinter
- VLC-based playback with ffplay fallback

## Features
- Add channels manually in JSON config
- Import `.m3u` playlist files
- Assign channels to specific MAC addresses
- Detect local MAC addresses automatically
- View and filter channels by selected MAC
- Open channel streams directly using VLC
- Save config automatically

## Requirements
- Python 3.9+
- VLC media player installed
- Python packages:
  - python-vlc
  - requests

Install dependencies:

```bash
pip install -r requirements.txt
```

On macOS, install VLC from https://www.videolan.org/vlc/

## Run

```bash
python app.py
```

## JSON config example

```json
{
  "00:11:22:33:44:55": [
    {"name": "RTV21", "url": "http://example.com/rtv21.m3u8"},
    {"name": "KTV", "url": "http://example.com/ktv.m3u8"}
  ],
  "aa:bb:cc:dd:ee:ff": [
    {"name": "Sport", "url": "http://example.com/sport.m3u8"}
  ]
}
```

## M3U import

Use the import button in the GUI or call:

```python
from app import import_m3u_file
import_m3u_file("playlist.m3u", "channels.json")
```

## Notes

- Mac address values are normalized to lowercase and trimmed
- RTMP streams must be supported by VLC
- Some streams require a valid user-agent or proper headers depending on provider
