# Build Instructions for Raylib 3D Game

## Prerequisites

### Windows
- Visual Studio 2022 or MinGW
- CMake 3.10+
- Git

### Linux (Ubuntu/Debian)
```bash
sudo apt-get update
sudo apt-get install -y cmake build-essential git libx11-dev libxrandr-dev libxinerama-dev libxcursor-dev libxi-dev libxxt-dev libxext-dev libxkbcommon-dev
```

### macOS
```bash
brew install cmake
```

## Building Locally

### Windows (Visual Studio)
```bash
mkdir build
cd build
cmake .. -G "Visual Studio 17 2022"
cmake --build . --config Release
# Executable will be at: bin/Release/raylib-3d-game.exe
```

### Windows (MinGW)
```bash
mkdir build
cd build
cmake .. -G "MinGW Makefiles"
cmake --build .
# Executable will be at: bin/raylib-3d-game.exe
```

### Linux & macOS
```bash
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
cmake --build .
# Executable will be at: bin/raylib-3d-game
```

## Running the Game

### Windows
```
bin/Release/raylib-3d-game.exe
```

### Linux & macOS
```bash
./bin/raylib-3d-game
```

## Game Controls

- **W/A/S/D** - Move horizontally
- **SPACE** - Move up
- **LEFT CTRL** - Move down
- **LEFT SHIFT** - Shoot
- **ESC** - Close game

## Game Mechanics

### Waves
- Each wave spawns progressively more enemies
- Wave 1: 7 enemies
- Wave 2: 9 enemies
- Wave 3+: 5 + (wave * 2) enemies

### Combat
- Shoot yellow bullets at red enemy cubes
- Each enemy takes 2 shots to destroy
- Enemies shoot back orange bullets
- Avoid colliding with enemies

### Scoring
- Each destroyed enemy: 100 points
- Try to survive as many waves as possible!

## Downloading Pre-compiled Binaries

If GitHub Actions has completed building:

1. Go to the repository on GitHub
2. Click on **Actions** tab
3. Select the latest build
4. Scroll down to "Artifacts"
5. Download:
   - `raylib-3d-game-windows` for Windows (.exe)
   - `raylib-3d-game-linux` for Linux
   - `raylib-3d-game-macos` for macOS

## Troubleshooting

### CMake not found
Make sure CMake is installed and in your PATH.

### raylib not found
The CMakeLists.txt will automatically download raylib 4.5.0 if not found locally.

### Build fails on Linux
Try updating your system and installing all dependencies:
```bash
sudo apt-get upgrade
sudo apt-get install -y libwayland-dev libxkbcommon-dev
```

### macOS M1/M2 (Apple Silicon)
The build should work natively, but if issues occur:
```bash
cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_OSX_ARCHITECTURES=arm64
```