# Adapter Practice

This repository contains a small Python example of the Adapter design pattern.
It shows how an `AudioPlayer` can expose a single `play()` interface while using
an adapter to work with a different player implementation for unsupported formats.

## What This Example Demonstrates

- Defining a common interface with an abstract base class
- Using an adapter to bridge incompatible interfaces
- Handling native and adapted media formats through one entry point
- A basic object adapter implementation in Python

## Project Structure

```text
Adapter Practice/
|- Basic/
|  |- ObjectAdapter
|  `- explanation.md
`- README.md
```

## Code Overview

The main example is in `Basic/ObjectAdapter`.

- `MediaPlayer`: abstract interface with a `play(audio_type, filename)` method
- `VLC_Player`: existing class with a different method, `play_vlc(...)`
- `MediaAdapter`: adapts `VLC_Player` to the `MediaPlayer` interface
- `AudioPlayer`: client-facing player that plays `mp3` directly and delegates other formats to the adapter

## How It Works

1. `AudioPlayer` receives a request through `play(audio_type, filename)`.
2. If the format is `mp3`, it handles playback directly.
3. For other formats like `vlc`, it forwards the request to `MediaAdapter`.
4. `MediaAdapter` translates the call to `VLC_Player.play_vlc(...)`.

This keeps the client code simple while allowing integration with a class that
does not follow the same interface.

## Run the Example

Make sure Python 3 is installed, then run:

```bash
python "Basic/ObjectAdapter"
```

## Example Output

```text
The mp3 is playing : mp3.song
The vlc is Playing: vlc.song
```

## Why Adapter Pattern Here

The Adapter pattern is useful when:

- you already have a working class with an incompatible method signature
- you want clients to use a consistent interface
- you want to add support for new implementations without changing client code too much

In this example, `AudioPlayer` does not need to know how `VLC_Player` works internally.
It simply uses the adapter through the common interface.

## Possible Improvements

- add support for more media types such as `mp4`
- validate unsupported formats explicitly
- rename `Basic/ObjectAdapter` to `Basic/ObjectAdapter.py` for easier execution and editor support
- add separate example files for class adapter and object adapter comparisons

## Requirements

- Python 3.x
- No external dependencies
