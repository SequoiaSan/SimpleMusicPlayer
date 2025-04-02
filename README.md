# Simple Music Player

A plugin for Unreal Engine designed to provide a straightforward background music player. With this plugin, you can trigger music tracks from anywhere in Blueprints, offering a seamless audio experience for your game.

### Features
- Continuous playback across maps without interruptions
- Variable real-time BPM (beats per minute) control without affecting pitch
- Playlist support
- Shuffle functionality
- Customizable track duration
- Smooth fade-out transitions between tracks

The **Simple Music Player** includes three primary nodes:
- **Play Track**: Plays a single track
- **Play Playlist**: Plays a predefined playlist
- **Play Cue**: Plays a prepared Sound Cue (simplified mode, no variable BPM support)

---

## Play Track

![image](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/play_track_node.png)

Designed to play a single track using a `SimpleMusicTrack` Blueprint.

### Node Inputs
- **Track Class**: Assign a Blueprint created from the `SimpleMusicTrack` class.
- **Loop**: If enabled, the track loops indefinitely.
- **Transition**: If enabled, the track continues playing across map/level changes without restarting.
- **Force Play**: If enabled, the track will restarts from the beginning when node executed, even if `Transition` is active.

### Creating a SimpleMusicTrack Blueprint
The `SimpleMusicTrack` Blueprint can be found here:  
![SimpleMusicTrack](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/simplemusictrack.png)

A newly created `SimpleMusicTrack` Blueprint has this thumbnail:  
![SimpleMusicTrack Thumbnail](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/simplemusictrack_thumbnail.png)

#### SimpleMusicTrack Structure and Options
![SimpleMusicTrack Structure](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/simplemusictrack_structure.png)

- **Audio File**: Select the desired Wave asset.
- **Optional Info**:
  - **Volume**: Set the playback volume (0.0 to 1.0).
  - **Base BPM**: Define the track’s base beats per minute.
  - **Max BPM**: Set the maximum BPM for variable speed playback.
  - **Time To Play**: Specify the duration (in seconds) the track plays. Ignored if `Loop` is enabled.
  - **Sound Class**: Assign a Sound Class to this track for audio mixing.

---

## Play Playlist

![Play Playlist Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/play_playlist_node.png)

Designed to play a sequence of tracks from a `SimpleMusicPlaylist` Blueprint.

### Node Inputs
- **Track Class**: Assign a Blueprint created from the `SimpleMusicPlaylist` class.
- **Transition**: If enabled, the playlist continues across map/level changes without restarting.
- **Time Per Track**: Default duration (in seconds) for each track in the playlist. Applies to tracks without a custom duration set in the `Optional Info` section.
- **Time To Fade**: Percentage of the track’s duration (e.g., 0.02 = 2%) at which fading begins when switching tracks. For example, a 2-minute track with 2% fade starts fading at 1:56. Applies to tracks without a custom fade out duration set in the `Optional Info` section.
- **Shuffle**: If enabled, tracks play in random order.
- **Force Play**: If enabled, the playlist restarts from the beginning when node executed, even if `Transition` is active.

### Creating a SimpleMusicPlaylist Blueprint
The `SimpleMusicPlaylist` Blueprint can be found here:  
![SimpleMusicPlaylist](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/simplemusicplaylist.png)

A newly created `SimpleMusicPlaylist` Blueprint has this thumbnail:  
![SimpleMusicPlaylist Thumbnail](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/simplemusicplaylist_thumbnail.png)

#### SimpleMusicPlaylist Structure and Options
![SimpleMusicPlaylist Structure](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/simplemusicplaylist_structure.png)

- **Audio File**: Select the desired Wave asset.
- **Optional Info**:
  - **Time To Play**: Duration (in seconds) the track loops. Overrides the node’s `Time Per Track`.
  - **Time To Fade Out**: Percentage of the track’s duration (e.g., 0.02 = 2%) at which fading begins. For example, a 2-minute track with 2% fade starts fading at 1:56.
  - **Preserve Position**: If enabled - during shuffle, this track retains its position in the playlist. Useful for ensuring a specific track (e.g., an intro) always plays first.
  - **Volume**: Set the playback volume (0.0 to 1.0).
  - **Base BPM**: Define the track’s base beats per minute.
  - **Max BPM**: Set the maximum BPM for variable speed playback.
- **Sound Class**: Assign a Sound Class to each track from playlist for audio mixing.

---

## Play Cue

![Play Cue Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/play_cue_node.png)

Designed to play a single track using a standard Unreal Engine Sound Cue.  
**Note**: This mode does not support variable BPM.

This is the simplest option, ideal for game jams or projects with minimal audio needs.

---

## Using the Transition Parameter

The `Transition` parameter ensures music persists across level or map changes without restarting. For example:
- **Scenario**: You have a Main Menu map and three level maps. You want the Main Menu music to play only in the Main Menu, but a Main Theme to play continuously across all three levels without reloading.
- **Setup**:
  - In the Main Menu, use a `Play Track` node with the Main Menu track and `Transition` disabled.
  - In each level map, use a `Play Track` node with the Main Theme track and `Transition` enabled.

### How Transition Works
- When `Transition` is enabled, the node checks the currently playing track, playlist, or cue:
  - If it matches the new node’s input, playback continues uninterrupted.
  - If it differs, the previous audio stops, and the new audio starts.
- **Compatibility**: `Transition` only works within the same node type (e.g., `Play Track` with `Play Track`). Mixing node types (e.g., `Play Track` with `Play Playlist`) restarts playback.
- **Matching Logic**:
  - `Play Track`: Compares the audio file.
  - `Play Playlist`: Compares the `SimpleMusicPlaylist` name.
  - `Play Cue`: Compares the Sound Cue file.

---

## OnTrackFinished Event

![OnTrackFinished Event](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/ontrackfinished_event.png)

The `OnTrackFinished` event triggers when a track completes or is stopped.  
**Note**: Tracks set to loop indefinitely will not fire this event.

---

## Additional Nodes

### Set Max BPM
![Set Max BPM Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/setmaxbpm.png)
Sets the maximum BPM for the currently playing track.

### Set New BPM Normalized
![Set New BPM Normalized Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/setnewbpmnormalized.png)
Adjusts BPM in real-time between `Base BPM` and `Max BPM` using a normalized input (0.0 to 1.0). Applies to the current track (`Play Track`) or all tracks in the playlist (`Play Playlist`).

### Set New BPM
![Set New BPM Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/setnewbpm.png)
Immediately sets the BPM to a specific value for the current track.

### Set Volume
![Set Volume Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/setvolume.png) 
Adjusts the volume of the currently playing track.

### Pause
![Pause Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/pause.png)  
Pauses the current music playback.

### Resume
![Resume Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/resume.png)   
Resumes paused music playback.

### Stop
![Stop Node](https://github.com/SequoiaSan/SimpleMusicPlayer/tree/main/images/stop.png)   
Stops the current music playback entirely.

---
