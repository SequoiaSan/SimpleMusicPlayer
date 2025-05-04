# Quick Start Guide

## Plugin Installation

1. Go to your Epic Games Launcher and open Unreal Engine tab on the left.
2. Proceed to Library tab (on top)
3. Scroll to the bottom of the page to Fab Library section (optionally click on refresh icon)

![Fab Library refresh icon](<images/quick_start/fab_refresh.png>)

4. Type in search box "Simple Music Player". You should see plugin in the list.

![Search results for Simple Music Player plugin](<images/quick_start/fab_plugin.png>)

5. Click on "Install to Engine" button near plugin.
6. Choose to which Unreal Engine version you want to install plugin.

![Plugin installation to Unreal Engine version](<images/quick_start/fab_plugin_install.png>)

**Congratulations! You installed the plugin!**

## Enable Plugin in Project

1. Open your project (note, your project should be using same Unreal Engine version in which you installed plugin)
2. Open menu "Edit" on the top. Choose "Plugins"
![Unreal Engine Plugins menu screenshot](<images/quick_start/ue_plugins.png>)
3. In a search box on the top of plugin manager type in `Simple Music Player`
4. Now you should see plugin in the list.

![Plugin Manager showing Simple Music Player plugin](<images/quick_start/ue_plugin_manager_search.png>)

5. Tick box on the left of the plugin. Now Unreal Engine would ask you to restart the editor to apply your changes.

![Prompt to restart Unreal Engine editor after enabling the plugin](<images/quick_start/ue_plugin_manager_tick.png>)

6. Restart Unreal Engine editor.

**Congratulations! You enabled Simple Music Plugin in your project!**

## Plugin Usage

We provide a small start example of how this plugin can be used, but it's not the only way. Plugin can be used almost in any kind of blueprint.

1. Create a `SoundCue` file with music
![Creating a SoundCue file with music_1](images/quick_start/soundcue_1.png)
![Creating a SoundCue file with music_2](images/quick_start/soundcue_1.png)
2. Open level blueprint
![Level blueprint example](images/quick_start/level_blueprint.png)
3. Right click on free space in level blueprint and type "Get SimpleMusicPlayer"
![Right-clicking in level blueprint to find 'Get SimpleMusicPlayer' node](images/quick_start/get_simplemusicplayer_node.png)
4. Add node `Get SimpleMusicPlayer`
![Adding the 'Get SimpleMusicPlayer' node in the level blueprint](images/quick_start/simplemusicplayer_node.png)
5. Grab an output of newly created SimpleMusicPlayer node and drop it somewhere in level blueprint
6. In opened submenu start typing "Play Cue"
![Adding 'Play Cue' node in level blueprint](images/quick_start/get_play_cue_node.png)
7. Add node `Play Cue`
![Adding the 'Play Cue' node in the level blueprint](images/quick_start/play_cue_node.png)
8. Grab execution node from `Event BeginPlay` event of level blueprint and attach it to `Play Cue` execution node
![Connecting Event BeginPlay to Play Cue node in level blueprint](images/quick_start/execute_play_cue_node.png)
9. In Play Cue's "Cue" drop-down field find your SoundCue and choose it
![Selecting a SoundCue in the Play Cue node's Cue drop-down field](images/quick_start/play_cue_node_drop_down.png)
10. Now hit play in Unreal Engine Editor and you should hear your soundCue play.
![Unreal Engine Editor playing the SoundCue](images/quick_start/start_game.png)

**Congratulations! You made it!**

Please, refer to our documentation to find out what all inputs in nodes do and what other nodes exist.
Also, check out our YouTube guide series on Simple Music Player to see its usage in action.