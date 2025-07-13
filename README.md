# iSAID-512Tiles

512×512 sliced image tiles and YOLO-format annotations derived from the iSAID aerial imagery dataset, created by **Marko Mihajlovic** for academic use in instance segmentation.

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
0: plane  
1: ship  
2: storage tank  
3: baseball diamond  
4: tennis court  
5: basketball court  
6: ground track field  
7: harbor  
8: bridge  
9: large vehicle  
10: small vehicle  
11: helicopter  
12: roundabout  
13: soccer ball field  
14: swimming pool
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
4. Generate YOLO-compatible annotations for each tile using bounding box conversion scripts.
5. Organize into `train`, `valid`, and `test` sets in YOLO folder structure.

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
  title={iSAID-512Tiles: A Sliced Aerial Image Dataset for Instance Segmentation},
  author={Marko Mihajlovic},
  year={2025},
  howpublished={\url{https://github.com/mihajlov39547/iSAID-Sliced-512}},
  note={Singidunum University, Belgrade, Serbia}
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

@ARTICLE{9560031,
  author={Ding, Jian and Xue, Nan and Xia, Gui-Song and Bai, Xiang and Yang, Wen and Yang, Michael and Belongie, Serge and Luo, Jiebo and Datcu, Mihai and Pelillo, Marcello and Zhang, Liangpei},
  journal={IEEE Transactions on Pattern Analysis and Machine Intelligence},
  title={Object Detection in Aerial Images: A Large-Scale Benchmark and Challenges},
  year={2021},
  volume={},
  number={},
  pages={1-1},
  doi={10.1109/TPAMI.2021.3117983}}

@InProceedings{Xia_2018_CVPR,
author = {Xia, Gui-Song and Bai, Xiang and Ding, Jian and Zhu, Zhen and Belongie, Serge and Luo, Jiebo and Datcu, Mihai and Pelillo, Marcello and Zhang, Liangpei},
title = {DOTA: A Large-Scale Dataset for Object Detection in Aerial Images},
booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
month = {June},
year = {2018}
}

@InProceedings{Ding_2019_CVPR,
author = {Jian Ding, Nan Xue, Yang Long, Gui-Song Xia, Qikai Lu},
title = {Learning RoI Transformer for Detecting Oriented Objects in Aerial Images},
booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
month = {June},
year = {2019}
}
```

---

## ⚠️ Notes

- Full-resolution iSAID and DOTA datasets must be downloaded separately.
- This repository contains only 512×512 sliced tiles and YOLO-format annotations.
- Use the iSAID Devkit to reproduce large image splits or evaluate performance against the benchmark.

---

Happy training!
