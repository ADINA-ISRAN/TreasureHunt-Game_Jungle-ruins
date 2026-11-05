# 🏛️ TREASURE HUNT: JUNGLE RUINS (3D Endless Runner)

**Run • Collect • Avoid • Survive**  
Created for Unity 6 / Unity 2022+ based directly on the **Treasure Hunt Game Design Presentation**.

---

## 🎮 Quick Start: How to Play in Unity

1. **Open Unity Hub**.
2. Click **Add** -> **Add project from disk**.
3. Select this folder: `C:\Users\HP\Downloads\TreasureHunt game`.
4. Select Unity Editor version **Unity 6 (6000.3 LTS)** or any installed 3D/URP editor.
5. Click **Open**.
6. When Unity opens:
   - All 4 scenes and required tags (`Player`, `Coin`, `Gem`, `Key`, `Obstacle`, `PowerUp`) are automatically verified and configured via `Assets/Editor/TreasureHuntSetup.cs`.
   - In the top menu bar, you will see a dedicated **`Treasure Hunt`** menu:
     - Click **`Treasure Hunt` -> `Rebuild All Scenes & Assets`** anytime to re-generate or refresh all 4 scenes.
     - Click **`Treasure Hunt` -> `Play GamePlay Scene Directly`** to jump straight into running!
     - Click **`Treasure Hunt` -> `Play Main Menu Scene`** to start from the title menu.

---

## 🌐 Instant Web Playable Preview (No Waiting)
You can also play the game immediately in your web browser!
- Double click **`PlayableWebPreview.html`** in this folder to launch the complete 3D endless runner directly in Chrome, Edge, or Firefox with full keyboard and swipe controls, 3D graphics, and real-time audio!

---

## 🕹️ Controls

| Action | Desktop Controls | Touch / Mobile / Mouse |
| :--- | :--- | :--- |
| **Move Left** | `A` or `Left Arrow` | Swipe Left / Drag Left |
| **Move Right** | `D` or `Right Arrow` | Swipe Right / Drag Right |
| **Jump** | `Space`, `W`, or `Up Arrow` | Swipe Up |
| **Slide** | `S` or `Down Arrow` | Swipe Down |
| **Pause** | `Esc` or `P` | Pause Button (HUD) |

---

## 🗺️ 4 Complete Game Scenes (As Defined in Slides)

### 1. `Scene 0: MainMenu.unity`
- **Features**: 3D Explorer display, Temple entrance, gold torchlight, and glowing treasure chest.
- **HUD**: Total saved Coins, Gems, and Best Run Distance.
- **Controls**: "START EXPEDITION" button with click SFX and fade transition to Stage Select.

### 2. `Scene 1: StageSelect.unity`
- **Features**: World exploration selector:
  - 🌿 **Jungle Ruins** *(Active Featured World)*
  - 🏜️ **Desert Temple**
  - 💎 **Lost Cave**
  - 🏴‍☠️ **Pirate Cove**
- **Action**: "PLAY JUNGLE RUINS" button plays audio and loads the Information screen.

### 3. `Scene 2: Information.unity`
- **Features**: Visual controls guide (Lane shifts, Jump, Slide, Collectibles, Power-ups).
- **Behavior**: Displays animated `LOADING...` prompt and automatically advances to Gameplay after 2.5s (or tap/Space to start immediately).

### 4. `Scene 3: GamePlay.unity`
- **Features**: Fast-paced 3D endless runner through ancient overgrown ruins.
- **Endless Generation**: `SegmentGenerator.cs` dynamically spawns modular ruin tracks, stone archways, and bridges.
- **Obstacles**: All 6 hazards from Slide 5:
  1. 📦 **Wooden Crate**: Lane barrier — jump over or dodge.
  2. ⚡ **Spike Trap**: Ground hazard — jump over.
  3. 🪵 **Rolling Spiked Log**: Suspended hazard — **slide under**!
  4. 🪨 **Rolling Boulder**: Massive stone rolling down a lane — dodge!
  5. 🌉 **Collapsing Bridge / Chasm**: Jump across gaps!
  6. 🛡️ **Spear Guard**: Ancient idol guardian standing in lane — dodge!
- **Collectibles & Treasures**:
  - 🪙 **Gold Coins**: +1 Coin counter, spins and floats upwards on collect.
  - 💎 **Sapphire Gems**: Rare gem pickups (+1 Gem).
  - 🗝️ **Golden Keys**: Unlocks ancient ruin treasure vaults.
  - 👑 **Treasure Chests**: Massive burst of bonus coins and gems.
- **Power-ups**:
  - 🧲 **Coin Magnet**: Draws coins from all lanes towards the player.
  - 🛡️ **Shield Bubble**: Protects the explorer from 1 fatal collision!
  - ⚡ **Speed Boost**: High-speed dash multiplier.
- **Game Over & Revive**:
  - Shows final Distance, Coins, and Best Score.
  - **Revive Button**: Costs 20 gems (as specified in presentation) to resurrect and continue!
  - **Retry Button**: Instantly restarts run.
  - **Main Menu Button**: Returns to title screen with progress saved.

---

## 📂 Project Architecture & C# Scripts

```
TreasureHunt game/
├── Packages/
│   └── manifest.json             # Unity package dependencies (uGUI, Audio, Physics, etc.)
├── ProjectSettings/
│   ├── ProjectVersion.txt        # Configured for Unity 6 (6000.3.28f1 LTS)
│   ├── EditorBuildSettings.asset # All 4 scenes registered in build order
│   └── TagManager.asset          # Tags: Player, Coin, Gem, Key, Obstacle, PowerUp
├── Assets/
│   ├── Audio/                    # Synthesized .wav audio assets:
│   │   ├── coin_pickup.wav       # Bright coin ding
│   │   ├── gem_pickup.wav        # Crystal chime
│   │   ├── key_pickup.wav        # Golden key fanfare
│   │   ├── jump.wav              # Upward whoosh
│   │   ├── slide.wav             # Gravelly skid
│   │   ├── collision.wav         # Heavy obstacle impact
│   │   ├── powerup.wav           # Rising power fanfare
│   │   ├── button_click.wav      # Snappy UI click
│   │   └── jungle_bgm.wav        # Looping tribal percussion & jungle drum rhythm
│   ├── Editor/
│   │   └── TreasureHuntSetup.cs  # Automated scene builder & setup tools
│   ├── Scenes/
│   │   ├── MainMenu.unity        # Scene 0
│   │   ├── StageSelect.unity     # Scene 1
│   │   ├── Information.unity     # Scene 2
│   │   └── GamePlay.unity        # Scene 3
│   └── Scripts/                  # All scripts from the PPT slides:
│       ├── MainMenuControl.cs    # Menu fade, camera, start button
│       ├── StageControls.cs      # Stage selection & transitions
│       ├── LoadToStage.cs        # Animated loading & scene progression
│       ├── PlayerMovement.cs     # Auto-forward run, lane shift, jump, slide, magnet, shield
│       ├── SegmentGenerator.cs   # Procedural track segment instantiator & recycler
│       ├── MasterLevelInfo.cs    # Global session counters & HUD updater
│       ├── SaveLoad.cs           # Persistent PlayerPrefs progress saving
│       ├── CollisionDetect.cs    # Shield check, obstacle crash, game over
│       ├── CollectCoin.cs        # Coin spin, pickup sound, upward float
│       ├── GemCollect.cs         # Gem spin, sparkle sound, collection
│       ├── KeyCollect.cs         # Antique key collector
│       ├── PowerUpCollect.cs     # Shield, Magnet, Speed Boost, Treasure Chest
│       ├── CollectableRotate.cs  # Smooth Y-axis spin & vertical bobbing
│       ├── CameraFollow.cs       # 3rd-person chase camera with lane smoothing
│       ├── ObstacleHazard.cs     # Behaviors for the 6 slide hazards
│       ├── GameUIManager.cs      # HUD, Pause dialog, Game Over & 20-gem Revive
│       ├── SoundManager.cs       # Central SFX & background music controller
│       └── JungleWorldBuilder.cs # Procedural 3D meshes, materials, and track segments
└── PlayableWebPreview.html       # Standalone 3D playable runner for any browser
```

---

## 🎯 Verification Checklist

- [x] **Jungle Ruins Theme**: Mossy stone road, ruined pillars, torchlight, lush atmosphere.
- [x] **Player Movement**: Auto-run forward, lane switching (A/D/Arrows/Swipes).
- [x] **Jump & Slide**: Jump over crates/spikes, slide under low rolling logs.
- [x] **Segment Generation**: Random endless track segments with automatic garbage collection.
- [x] **Collectibles**: Coins, Blue Gems, Golden Keys, and Treasure Chests.
- [x] **6 Hazards**: Crate, Spike Trap, Rolling Boulder, Collapsing Bridge/Pit, Rolling Log, Spear Guard.
- [x] **Power-ups**: Magnet, Shield, Speed Boost, Multiplier.
- [x] **Game Over & Revive**: Revive with 20 gems or retry.
- [x] **Score & HUD**: Coins, gems, keys, distance meters, and persistent PlayerPrefs highscores.
- [x] **Full Unity & Browser Compatibility**: Ready to play in Unity Editor and browser!
