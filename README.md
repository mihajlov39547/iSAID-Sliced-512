[![GitHub release](https://img.shields.io/github/v/release/mihajlov39547/iSAID-Sliced-512)](https://github.com/mihajlov39547/iSAID-Sliced-512/releases)

[![DOI](https://zenodo.org/badge/1019023896.svg)](https://doi.org/10.5281/zenodo.18076179)

# iSAID-512Tiles

512×512 sliced image tiles and YOLO-format annotations derived from the iSAID aerial imagery dataset, created by **mihajlov39547** for academic use in instance segmentation.

---

## 📚 Dataset Overview

This dataset consists of approximately **10,000 image tiles** derived from the iSAID dataset, which itself is based on DOTA-v1.0.

- **Author**: Marko Mihajlovic  
- **Affiliation**: Singidunum University, Belgrade, Serbia  
- **GitHub**: [https://github.com/mihajlov39547/iSAID-Sliced-512](https://github.com/mihajlov39547/iSAID-Sliced-512)

- **Original imagery source**:  
  DOTA-v1.0 dataset, sourced from Google Earth, GF‑2, and JL‑1 satellites.  
  The iSAID dataset builds upon DOTA by providing instance-level pixel annotations for segmentation tasks.  
  This tile dataset (iSAID-512Tiles) is built on top of the iSAID dataset by slicing large images into 512×512 patches.

---

## 🗂️ Repository Contents

```
iSAID-512Tiles/
├── train/
│   ├── images/
│   └── labels/
├── valid/
│   ├── images/
│   └── labels/
├── test/
│   ├── images/
│   └── labels/
├── LICENSE
└── README.md
```

- `images/` contains 512×512 `.jpg` image tiles  
- `labels/` contains YOLO-format `.txt` annotation files  
- File naming format: `tile_000022_jpg.rf.963f01347ea22d1139e70faf42fd3065.jpg`, `tile_000022_jpg.rf.963f01347ea22d1139e70faf42fd3065.txt`

---

## 🏷️ Object Categories

The following categories are inherited from iSAID (which uses DOTA's classes):

```
0:  small vehicle
1:  large vehicle
2:  plane
3:  storage tank
4:  ship
5:  harbor
6:  swimming pool
7:  soccer ball field
8:  tennis court
9:  ground track field
10: baseball diamond
11: bridge
12: basketball court
13: roundabout
14: helicopter
```

---

## ⚙️ Annotation Format

Each `.txt` annotation file uses YOLO normalized format:

```
<class_id> <x_center> <y_center> <width> <height>
```

All values are normalized between 0 and 1.

---

## 🔧 How to Generate Test Dataset

1. Download full-resolution iSAID and DOTA datasets.
2. Use the official devkit:  
   [https://github.com/CAPTAIN-WHU/iSAID_Devkit](https://github.com/CAPTAIN-WHU/iSAID_Devkit)
3. Use the `split.py` script to divide large iSAID images into 512×512 tiles.
4. Organize into `test` sets in YOLO folder structure.

---

## 🧾 test_info.json

The `test_info.json` file provides metadata for the test image tiles included in the dataset.

### Contents

Each entry in `test_info.json` includes:

- `file_name`: Name of the tile image (e.g., `tile_000123.jpg`)
- `id`: Unique image ID
- `width`, `height`: Dimensions of the tile (typically 512×512)
- `orig_img`: Name of the original large image from iSAID (e.g., `P0001.png`)
- `orig_width`, `orig_height`: Dimensions of the original image
- `x_offset`, `y_offset`: Coordinates of the tile within the original image

### Example Entry

```json
{
  "file_name": "tile_000123.jpg",
  "id": 123,
  "width": 512,
  "height": 512,
  "orig_img": "P0001.png",
  "orig_width": 4000,
  "orig_height": 4000,
  "x_offset": 1024,
  "y_offset": 512
}
```

### Purpose

- Enables mapping tile predictions back to full-sized iSAID images.
- Useful for merging tiles, visualization, or structured evaluation.
- No annotation data is included in this file—it is strictly for tile metadata.

---

## 🧪 Evaluation & Competition

To evaluate results on the original iSAID benchmark:

- Submit a `.json` file (COCO-style) to the official iSAID evaluation server.
- Receive mAP and per-class AP via email.
- One submission allowed per user per day.
- A method description (≥ 120 words) in English is required.

For local evaluation, use the official devkit’s script:

```bash
python evaluate/evaluate.py
```

---

## 📜 License

**Creative Commons Attribution‑NonCommercial 4.0 International (CC BY‑NC 4.0)**

- ✅ Academic/research use: Allowed with attribution  
- ❌ Commercial use: Prohibited

See the full license in the `LICENSE` file.

---

## 📖 Citation

If you use this dataset, please cite:

```bibtex
@misc{mihajlovic2025isaid512tiles,
  title        = {iSAID-512Tiles: A Sliced Aerial Image Dataset for Instance Segmentation},
  author       = {Mihajlovic, Marko},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.18076179},
  url          = {https://doi.org/10.5281/zenodo.18076179},
  note         = {Dataset},
}
```

Also cite the following original datasets:

```bibtex
@inproceedings{waqas2019isaid,
  title={iSAID: A Large-scale Dataset for Instance Segmentation in Aerial Images},
  author={Zamir, Syed Waqas and Arora, Aditya and Gupta, Akshita and Khan, Salman and Sun, Guolei and Shahbaz Khan, Fahad and Zhu, Fan and Shao, Ling and Xia, Gui-Song and Bai, Xiang},
  booktitle={CVPR Workshops},
  year={2019}
}

@inproceedings{xia2018dota,
  title={DOTA: A Large-Scale Dataset for Object Detection in Aerial Images},
  author={Xia, Gui-Song and Bai, Xiang and et al.},
  booktitle={CVPR},
  year={2018}
}
```

---

## ⚠️ Notes

- Full-resolution iSAID and DOTA datasets must be downloaded separately.
- This repository contains only 512×512 sliced tiles and YOLO-format annotations.
- Use the iSAID Devkit to reproduce large image splits or evaluate performance against the benchmark.

---

Happy training!
