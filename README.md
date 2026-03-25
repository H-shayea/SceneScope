# SceneScope

<p align="center">
  <img src="images/readmeBG.png" alt="SceneScope hero" width="100%" />
</p>

<p align="center">
  Local-first desktop software for visualizing and exploring trajectory, V2X, and scene-based mobility datasets.
</p>

<p align="center">
  <strong>Dataset visualization</strong> · <strong>Scene exploration</strong> · <strong>Trajectory analysis</strong>
</p>

## Overview

SceneScope is a local-first desktop application designed for exploring mobility datasets. This repository hosts the public releases and official binaries for SceneScope.

## What SceneScope Supports

### Current Capabilities

- local dataset discovery and registration in the desktop app
- automatic detection of supported dataset families
- scene playback with timeline controls
- map, basemap, and scene-image visualization
- agent trajectories and bounding-box overlays
- dataset-specific analytics and inspector panels
- persistent local metadata and app state

### Platform Status

- **macOS**: Available in Releases (Apple Silicon, macOS 11+)
- **Windows**: Coming soon
- **Linux**: Coming soon

### Supported Dataset Families

SceneScope currently supports mapping and visualizing:

- `V2X-Traj`
- `V2X-Seq`
- `inD`
- `SinD`
- `CPM Objects / Consider.it`

## Installation

To install SceneScope on your Mac:

1. Navigate to the [Releases page](https://github.com/H-shayea/SceneScope/releases) of this repository.
2. Download the latest `SceneScope.dmg` file.
3. Open the DMG and drag SceneScope to your Applications folder.
4. *Note: If macOS blocks the app on first launch, Right-click the app and choose **Open**, or go to System Settings > Privacy & Security > Open Anyway.*

## License

SceneScope is licensed under the MIT License. See [LICENSE](LICENSE).
