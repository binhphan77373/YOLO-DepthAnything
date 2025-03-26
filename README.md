**YOLO-3D**

Hệ thống phát hiện đối tượng 3D thời gian thực kết hợp YOLOv11 để phát hiện đối tượng với Depth Anything v2 để ước tính chiều sâu, tạo ra các hộp 3D giả và trực quan hóa.

**Tính năng**

- Phát hiện đối tượng thời gian thực sử dụng YOLOv11
- Ước tính chiều sâu sử dụng Depth Anything v2
- Trực quan hóa hộp 3D
- Trực quan hóa từ góc nhìn chim (BEV)
- Khả năng theo dõi đối tượng
- Hỗ trợ tệp video và đầu vào webcam
- Cài đặt kích thước mô hình có thể điều chỉnh để cân bằng hiệu suất/độ chính xác

**Yêu cầu**

- Python 3.8+
- PyTorch 2.0+
- OpenCV
- NumPy
- Các phụ thuộc khác có trong tệp requirements.txt

**Cài đặt**

Clone kho mã nguồn này:

```
git clone https://github.com/binhphan77373/YOLO-DepthAnything.git
cd YOLO-DepthAnything
```

Cài đặt các phụ thuộc:

```
pip install -r requirements.txt
```

Tải mô hình trọng số (sẽ được tải tự động khi chạy lần đầu tiên)

**Sử dụng**

Chạy tệp chính:

```
python run.py
```

**Tùy chọn cấu hình**

Bạn có thể thay đổi các tham số sau trong tệp `run.py`:

**Đầu vào/Đầu ra**:
- `source`: Đường dẫn đến tệp video đầu vào hoặc chỉ số webcam (0 cho camera mặc định)
- `output_path`: Đường dẫn đến tệp video đầu ra

**Cài đặt mô hình**:
- `yolo_model_size`: Kích thước mô hình YOLOv11 ("nano", "small", "medium", "large", "extra")
- `depth_model_size`: Kích thước mô hình Depth Anything v2 ("small", "base", "large")

**Cài đặt phát hiện**:
- `conf_threshold`: Ngưỡng độ tin cậy cho phát hiện đối tượng
- `iou_threshold`: Ngưỡng IoU cho NMS
- `classes`: Lọc theo lớp, ví dụ: [0, 1, 2] cho các lớp cụ thể, None cho tất cả các lớp

**Tính năng bật/tắt**:
- `enable_tracking`: Bật theo dõi đối tượng
- `enable_bev`: Bật trực quan hóa
- `enable_pseudo_3d`: Bật trực quan hóa 3D

**Cấu trúc dự án**

```
YOLO-3D/
│── run.py                  # Tệp chính
│── detection_model.py      # Phát hiện đối tượng YOLOv11
│── depth_model.py          # Ước tính chiều sâu Depth Anything v2
│── bbox3d_utils.py         # Tiện ích hộp 3D
├── requirements.txt        # Các phụ thuộc của dự án
└── README.md            
```

**Cách hoạt động**

1. **Phát hiện đối tượng**: YOLOv11 phát hiện đối tượng trong khung hình và cung cấp các hộp 2D
2. **Ước tính chiều sâu**: Depth Anything v2 tạo bản đồ chiều sâu cho toàn bộ khung hình
3. **Ước tính hộp 3D**: Kết hợp hộp 2D với thông tin chiều sâu để tạo ra các hộp 3D
4. **Trực quan hóa**: Hiển thị các hộp 3D và góc nhìn để hiểu rõ hơn về không gian
