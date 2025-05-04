# Quick Start Guide

## Plugin Installation

1. Go to your Epic Games Launcher and open Unreal Engine tab on the left.
2. Proceed to Library tab (on top)
3. Scroll to the bottom of the page to Fab Library section (optionally click on refresh icon)

<img src="images/quick_start/fab_refresh.png" alt="Fab Library refresh icon" width="200" />

4. Type in search box "Simple Music Player". You should see plugin in the list.

<img src="images/quick_start/fab_plugin.png" alt="Search results for Simple Music Player plugin" width="600" />

5. Click on "Install to Engine" button near plugin.
6. Choose to which Unreal Engine version you want to install plugin.

<img src="images/quick_start/fab_plugin_install.png" alt="Plugin installation to Unreal Engine version" width="600" />

**Congratulations! You installed the plugin!**

## Enable Plugin in Project

1. Open your project (note, your project should be using same Unreal Engine version in which you installed plugin)
2. Open menu "Edit" on the top. Choose "Plugins"
<img src="images/quick_start/ue_plugins.png" alt="Unreal Engine Plugins menu screenshot" width="600" />
3. In a search box on the top of plugin manager type in `Simple Music Player`
4. Now you should see plugin in the list.

<img src="images/quick_start/ue_plugin_manager_search.png" alt="Plugin Manager showing Simple Music Player plugin" width="600" />

5. Tick box on the left of the plugin. Now Unreal Engine would ask you to restart the editor to apply your changes.

<img src="images/quick_start/ue_plugin_manager_tick.png" alt="Prompt to restart Unreal Engine editor after enabling the plugin" width="600" />

6. Restart Unreal Engine editor.

**Congratulations! You enabled Simple Music Plugin in your project!**

## Plugin Usage

We provide a small start example of how this plugin can be used, but it's not the only way. Plugin can be used almost in any kind of blueprint.

1. Create a `SoundCue` file with music
<img src="images/quick_start/soundcue_1.png" alt="Creating a SoundCue file with music_1" width="600" />
<img src="images/quick_start/soundcue_1.png" alt="Creating a SoundCue file with music_2" width="600" />
2. Open level blueprint
<img src="images/quick_start/level_blueprint.png" alt="Level blueprint example" width="600" />
3. Right click on free space in level blueprint and type "Get SimpleMusicPlayer"
<img src="images/quick_start/get_simplemusicplayer_node.png" alt="Right-clicking in level blueprint to find 'Get SimpleMusicPlayer' node" width="600" />
4. Add node `Get SimpleMusicPlayer`
<img src="images/quick_start/simplemusicplayer_node.png" alt="Adding the 'Get SimpleMusicPlayer' node in the level blueprint" width="600" />
5. Grab an output of newly created SimpleMusicPlayer node and drop it somewhere in level blueprint
6. In opened submenu start typing "Play Cue"
<img src="images/quick_start/get_play_cue_node.png" alt="Adding 'Play Cue' node in level blueprint" width="600" />
7. Add node `Play Cue`
<img src="images/quick_start/play_cue_node.png" alt="Adding the 'Play Cue' node in the level blueprint" width="600" />
8. Grab execution node from `Event BeginPlay` event of level blueprint and attach it to `Play Cue` execution node
<img src="images/quick_start/execute_play_cue_node.png" alt="Connecting Event BeginPlay to Play Cue node in level blueprint" width="600" />
9. In Play Cue's "Cue" drop-down field find your SoundCue and choose it
<img src="images/quick_start/play_cue_node_drop_down.png" alt="Selecting a SoundCue in the Play Cue node's Cue drop-down field" width="600" />
10. Now hit play in Unreal Engine Editor and you should hear your soundCue play.
<img src="images/quick_start/start_game.png" alt="Unreal Engine Editor playing the SoundCue" width="600" />

**Congratulations! You made it!**

Please, refer to our documentation to find out what all inputs in nodes do and what other nodes exist.
Also, check out our YouTube guide series on Simple Music Player to see its usage in action.