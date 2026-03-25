# SceneScope — macOS User Guide

A step-by-step guide for installing SceneScope on your Mac and loading your first dataset.

---

## Table of Contents

1. [System Requirements](#system-requirements)
2. [Download & Install](#download--install)
3. [Handling the macOS Security Warning](#handling-the-macos-security-warning)
4. [Preparing Your Datasets](#preparing-your-datasets)
5. [Importing Datasets into SceneScope](#importing-datasets-into-scenescope)
6. [Troubleshooting](#troubleshooting)

---

## System Requirements

| Requirement     | Minimum                          |
| --------------- | -------------------------------- |
| **Mac chip**    | Apple Silicon (M1, M2, M3, M4)  |
| **macOS**       | macOS 11 (Big Sur) or newer      |
| **Disk space**  | ~200 MB for the app              |

---

## Download & Install

1. Go to the [Releases](https://github.com/H-shayea/SceneScope/releases) page.
2. Under the latest release, download **SceneScope.dmg**.
3. Open the downloaded `.dmg` file — a Finder window will appear showing the SceneScope app icon and an "Applications" shortcut.
4. **Drag the SceneScope icon into the Applications folder.**
5. Eject the DMG (right-click → Eject) — you can also delete the `.dmg` file now, you no longer need it.

---

## Handling the macOS Security Warning

> **Why does this happen?**
> SceneScope is an independently distributed research tool. It is not published through the Mac App Store and is not notarized by Apple, so macOS treats it as an "unidentified developer" app the first time you open it. **This is normal and expected.** The warning only appears once.

When you try to open SceneScope for the first time, macOS will show one of these messages:

- _"SceneScope can't be opened because it is from an unidentified developer."_
- _"SceneScope can't be opened because Apple cannot check it for malicious software."_

### How to bypass (Method 1 — Right-click Open)

This is the fastest way and works on all macOS versions:

1. Open **Finder** and go to **Applications**.
2. Find **SceneScope** in the list.
3. **Right-click** (or Control-click) on the SceneScope icon.
4. Select **"Open"** from the context menu.
5. A new dialog will appear with an **"Open"** button — click it.
6. macOS will remember your choice. From now on, you can open SceneScope normally by double-clicking.

### How to bypass (Method 2 — System Settings)

Use this method if the right-click approach does not show the "Open" button:

1. Try to open SceneScope normally (double-click). macOS will block it.
2. Open **System Settings** (Apple menu  → System Settings).
3. Go to **Privacy & Security** (scroll down in the left sidebar).
4. Scroll down to the **Security** section.
5. You will see a message: _"SceneScope was blocked from use because it is not from an identified developer."_
6. Click **"Open Anyway"**.
7. Enter your Mac password or use Touch ID when prompted.
8. SceneScope will now launch. Future launches will work normally.

### How to bypass (Method 3 — Terminal)

For advanced users who prefer the command line:

```bash
xattr -cr /Applications/SceneScope.app
```

This removes all quarantine attributes. After running this command, SceneScope opens normally.

---

## Preparing Your Datasets

Before importing datasets into SceneScope, you need to organize them on your disk. SceneScope expects a specific folder structure.

### Step 1: Create a main datasets folder

Create one parent folder anywhere on your Mac to hold all your datasets. For example:

```
~/Desktop/Datasets/
```

or

```
~/Documents/Datasets/
```

### Step 2: Place each dataset inside its own subfolder

Each dataset should sit in its own folder inside your main `Datasets` directory. The exact subfolder name is up to you, but the **contents** must follow the structure that each dataset provides when you download it.

Here is an example layout with two datasets:

```
Datasets/
├── ConsiderIt/
│   ├── Camera&LiDAR/
│   │   ├── train/
│   │   └── val/
│   └── Maps/
│       └── ...
│
├── V2X-Traj/
│   ├── train/
│   │   ├── scene_001.json
│   │   ├── scene_002.json
│   │   └── ...
│   ├── val/
│   └── maps/
│       └── ...
│
├── inD/
│   ├── data/
│   │   ├── 00_tracks.csv
│   │   ├── 00_tracksMeta.csv
│   │   └── ...
│   └── maps/
│       └── ...
│
└── ...
```

### Supported dataset families

SceneScope currently supports these dataset families:

| Dataset        | Family ID      | Typical folder contents                  |
| -------------- | -------------- | ---------------------------------------- |
| V2X-Traj       | `v2x-traj`     | Scene JSON files + HD maps               |
| V2X-Seq        | `v2x-seq`      | Sequence data + maps                     |
| inD            | `ind`          | Track CSV files + recording meta + maps  |
| SinD           | `sind`         | Track CSV files + recording meta + maps  |
| ConsiderIt CPM | `cpm-objects`  | Camera & LiDAR folders + Maps            |

> **Tip:** You do not need to rename your folders to match these IDs. SceneScope will automatically detect which dataset family each folder belongs to based on its contents.

---

## Importing Datasets into SceneScope

1. Launch **SceneScope**.
2. In the left sidebar, click **Import Dataset**.
3. You have two options:
   - **Click "Choose Folder…"** and navigate to your main `Datasets` folder (e.g. `~/Desktop/Datasets`), then click **Open**.
   - **Or type the path manually** in the text box (e.g. `/Users/yourname/Desktop/Datasets`) and click **Import Datasets**.
4. SceneScope will scan the folder and all subfolders, automatically detecting every supported dataset inside.
5. A summary will appear showing which datasets were found and imported.
6. Imported datasets will now appear in the **Library** and **Connected** sections of the home screen.

### Loading a single dataset

If you only want to import one specific dataset instead of the entire parent folder, simply point SceneScope to that dataset's own folder instead:

- Example: Choose `~/Desktop/Datasets/ConsiderIt` directly.

SceneScope will detect it and import just that one dataset.

---

## Troubleshooting

### "No supported datasets were found"

- Make sure you selected the correct folder. You can point to either the parent folder (e.g. `Datasets/`) or a specific dataset folder (e.g. `Datasets/ConsiderIt/`).
- Verify the dataset files are actually inside the folder and not nested in an extra subfolder (sometimes unzipping creates a double-nested folder).
- Check that you are using a supported dataset (see the table above).

### SceneScope won't open at all

- Make sure you followed the [security bypass steps](#handling-the-macos-security-warning).
- If you see a "damaged" error, run in Terminal:
  ```bash
  xattr -cr /Applications/SceneScope.app
  ```

### The app is slow to start

- The first launch takes a few extra seconds while macOS verifies the app. Subsequent launches are faster.
- If you have a very large number of datasets, the initial scan may take a moment.

---

**Need help?** Open an issue on the [GitHub repository](https://github.com/H-shayea/SceneScope/issues).
