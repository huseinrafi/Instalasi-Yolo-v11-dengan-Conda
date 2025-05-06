# 🦾 YOLOv8 Custom Object Detection

Tutorial ini menunjukkan cara melakukan pelatihan (training) model YOLOv8 untuk mendeteksi objek dari dataset custom. perlu diingat untuk sudah menginstall Python, YOLO dan pytorch

---

## 📁 Struktur Dataset

Pastikan dataset kamu dalam format berikut:

```
dataset/
├── images/
│   ├── train/
│   └── val/
├── labels/
│   ├── train/
│   └── val/
```

Setiap file gambar (`.jpg`, `.png`, dll) harus memiliki file label `.txt` dengan nama yang sama di folder `labels/`.

### Format Label:
Setiap baris dalam file `.txt` adalah:
```
<class_id> <x_center> <y_center> <width> <height>
```
- Semua nilai dalam format relatif (0–1)
- Koordinat dihitung relatif terhadap ukuran gambar

Gunakan alat seperti:
- [LabelImg](https://github.com/tzutalin/labelImg)
- [Roboflow](https://roboflow.com)

Dataset sudah disediakan di atas.

---

## 📝 Konfigurasi Dataset (`data.yaml`)

Contoh isi `data.yaml`:

```yaml
path: ../dataset
train: images/train
val: images/val

nc: 2  # jumlah class
names: ['orang', 'motor']  # sesuaikan dengan nama kelasmu
```

---

> Pastikan Python ≥ 3.8 dan PyTorch sudah terinstall

---

## 🚀 Training Model

Jalankan perintah berikut untuk memulai training:

```bash
yolo detect train model=yolov8n.pt data=dataset.yaml epochs=50 imgsz=640
```

### Penjelasan Parameter:
- `--img`: Ukuran gambar input (misalnya 640)
- `--epochs`: Jumlah epoch
- `--data`: Path ke `data.yaml`
- `--weights`: Model awal (gunakan `yolov8n.pt` untuk model ringan)
- `--name`: Nama folder output training di `runs/train/`

---

## 📈 Melihat Hasil Training

Setelah training selesai:
- Hasil disimpan di: `runs/train/custom_yolo/`
- Model terbaik: `weights/best.pt`
- Grafik performa: `results.png`

---



## 🔗 Referensi

- [YOLOv8 Quickstart Ultralytics]([https://github.com/ultralytics/yolov5](https://docs.ultralytics.com/quickstart/))
