# 🚗 Parking Lot Image Classifier with YOLOv8

This project uses the **Ultralytics YOLOv8 image classification model** to detect parking lot conditions from images. It was built and trained on a Jetson Nano for real-time edge inference.

## ✅ Training the Model

To train the model on your dataset:

```bash
yolo task=classify mode=train model=yolov8n-cls.pt data=dataset epochs=50 imgsz=224
```

* `yolov8n-cls.pt` is the base classification model (nano version).
* `dataset` should follow the standard classification folder format:

  ```
  dataset/
  ├── train/
  │   ├── class_0/
  │   └── class_1/
  ├── val/
  │   ├── class_0/
  │   └── class_1/
  ```

## 🧪 Validating the Model

To validate the trained model on a test set:

```bash
yolo task=classify mode=val model=runs/classify/train3/weights/best.pt data=/home/nvidia11/ParkingLot_Detecter/dataset
```

## 📷 Running Predictions

To classify new images:

```bash
yolo task=classify mode=predict model=runs/classify/train3/weights/best.pt source=/home/nvidia11/ParkingLot_Detector/runs/classify/test1
```

* Output predictions will be saved in the `runs/classify/predict` folder.

## 📤 Exporting the Model

Export the trained model for deployment in various formats:

```bash
yolo export model=runs/classify/train3/weights/best.pt format=onnx
```

Supported formats: `onnx`, `torchscript`, `openvino`, etc.

## 📊 Visualizing Training

Training results, accuracy plots, and loss curves are saved in:

```
runs/classify/train3/
```

Open with:

```bash
xdg-open runs/classify/train3/results.png
```

## 🚀 Hardware

* **Jetson Nano**
* Python 3.10
* Torch 2.1
* YOLOv8 via Ultralytics

## 📌 Notes

* Make sure your dataset is well-labeled and balanced.
* Adjust the model type (`yolov8n-cls.pt`, `yolov8s-cls.pt`, etc.) based on hardware.

---
