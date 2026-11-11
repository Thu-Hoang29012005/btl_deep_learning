# 🍔 FOODVISION AI
## Hệ thống nhận dạng và phân loại hình ảnh món ăn bằng Deep Learning

## 1. Giới thiệu dự án

FoodVision AI là hệ thống nhận dạng và phân loại hình ảnh món ăn được xây dựng bằng các phương pháp Deep Learning và Computer Vision.

Hệ thống cho phép người dùng tải lên một hình ảnh món ăn. Sau đó, mô hình sẽ phân tích hình ảnh, dự đoán món ăn thuộc lớp nào và hiển thị xác suất dự đoán tương ứng.

Dự án được thực hiện trong khuôn khổ bài tập lớn môn Deep Learning.

## 2. Mục tiêu dự án

- Xây dựng hệ thống phân loại hình ảnh món ăn sử dụng Deep Learning.
- Tìm hiểu và triển khai các mô hình CNN.
- Ứng dụng Transfer Learning với mô hình ResNet18.
- So sánh hiệu quả giữa các mô hình được huấn luyện.
- Đánh giá chất lượng mô hình bằng các chỉ số phù hợp.
- Xây dựng giao diện trực quan bằng Streamlit để người dùng trải nghiệm hệ thống.

## 3. Phạm vi bài toán

Dự án sử dụng bộ dữ liệu Food-101 và lựa chọn 10 lớp món ăn để xây dựng mô hình phân loại.

### Danh sách 10 lớp món ăn

| STT | Tên lớp |
|---|---|
| 1 | Hamburger |
| 2 | Pizza |
| 3 | Sushi |
| 4 | French Fries |
| 5 | Ice Cream |
| 6 | Chocolate Cake |
| 7 | Chicken Wings |
| 8 | Caesar Salad |
| 9 | Hot Dog |
| 10 | Waffles |

### Quy mô dữ liệu

| Tập dữ liệu | Số lượng ảnh |
|---|---:|
| Training | 6.000 |
| Validation | 1.500 |
| Testing | 2.500 |
| **Tổng cộng** | **10.000** |

Mỗi hình ảnh thuộc một trong 10 lớp món ăn đã lựa chọn.

## 4. Công nghệ sử dụng

| Công nghệ | Mục đích |
|---|---|
| Python | Ngôn ngữ lập trình chính |
| PyTorch | Xây dựng và huấn luyện mô hình Deep Learning |
| Torchvision | Xử lý ảnh và sử dụng mô hình pretrained |
| NumPy | Xử lý dữ liệu số |
| Pandas | Phân tích dữ liệu |
| Scikit-learn | Đánh giá mô hình |
| Matplotlib | Trực quan hóa kết quả |
| Streamlit | Xây dựng giao diện web |
| Google Colab | Môi trường huấn luyện mô hình |
| NVIDIA T4 GPU | Tăng tốc quá trình huấn luyện |

## 5. Các mô hình được triển khai

Dự án thực hiện ba mô hình để so sánh kết quả phân loại:

### 5.1. CNN Baseline

Xây dựng mô hình CNN cơ bản từ đầu, sử dụng các lớp tích chập để trích xuất đặc trưng hình ảnh và lớp phân loại để dự đoán 10 lớp món ăn.

### 5.2. ResNet18 Frozen

Sử dụng kiến trúc ResNet18 đã được huấn luyện trước trên ImageNet. Các lớp trích xuất đặc trưng được đóng băng, chỉ huấn luyện lớp phân loại cuối cùng.

### 5.3. ResNet18 Fine-tuning

Tiếp tục sử dụng ResNet18 pretrained, mở khóa layer4 và lớp phân loại cuối cùng để mô hình thích nghi tốt hơn với bộ dữ liệu Food-101 đã lựa chọn.

## 6. Kết quả thực nghiệm

Kết quả đánh giá trên tập kiểm tra:

| Mô hình | Accuracy | Macro-F1 |
|---|---:|---:|
| CNN Baseline | 47.56% | 44.99% |
| ResNet18 Frozen | 89.72% | 89.68% |
| ResNet18 Fine-tuning | **91.36%** | **91.34%** |

**Nhận xét:** ResNet18 Fine-tuning đạt kết quả tốt nhất với Accuracy 91.36% và Macro-F1 91.34%. Đây là mô hình được lựa chọn để tích hợp vào ứng dụng nhận dạng món ăn.

## 7. Cấu trúc thư mục dự án

```text
FoodVision/
│
├── app/
│   └── app.py
│
├── src/
│   ├── model.py
│   ├── model_resnet18.py
│   ├── model_resnet18_finetune.py
│   └── ...
│
├── data/
│   ├── raw/
│   └── processed/
│
├── models/
│   └── resnet18_finetune_best.pth
│
├── results/
│   ├── figures/
│   ├── reports/
│   └── ...
│
├── main.py
├── requirements.txt
└── README.md
```

*Lưu ý: Đây là cấu trúc mô tả các thư mục chính. Các tệp bên trong cần được đối chiếu với dự án thực tế.*

## 8. Hướng dẫn cài đặt và chạy chương trình

### Bước 1. Mở dự án

Mở thư mục FoodVision bằng Visual Studio Code.

### Bước 2. Tạo môi trường ảo

Mở Terminal trong VS Code và chạy:

```bash
python -m venv venv
```

### Bước 3. Kích hoạt môi trường ảo

Trên Windows:

```bash
venv\Scripts\activate
```

### Bước 4. Cài đặt thư viện

```bash
pip install -r requirements.txt
```

### Bước 5. Kiểm tra mô hình đã huấn luyện

Đảm bảo file trọng số mô hình đã được đặt đúng vị trí:

```text
models/resnet18_finetune_best.pth
```

### Bước 6. Khởi chạy ứng dụng

Tại thư mục gốc FoodVision, chạy lệnh:

```bash
streamlit run app/app.py
```

Sau khi chạy thành công, ứng dụng sẽ được mở trên trình duyệt thông qua địa chỉ localhost do Streamlit cung cấp.

## 9. Các chức năng của hệ thống

- Tải lên hình ảnh món ăn từ thiết bị.
- Hiển thị hình ảnh được tải lên.
- Nhận dạng và phân loại hình ảnh bằng mô hình ResNet18 Fine-tuning.
- Hiển thị tên món ăn được dự đoán.
- Hiển thị xác suất dự đoán của các lớp.
- Hỗ trợ xóa ảnh hiện tại và lựa chọn ảnh khác.
- Hiển thị thông tin mô hình và môi trường hệ thống.

## 10. Phương pháp đánh giá

Các chỉ số và phương pháp được sử dụng trong quá trình đánh giá:

- **Accuracy:** Tỷ lệ dự đoán chính xác trên tổng số mẫu kiểm tra.
- **Macro-F1:** Trung bình F1-score của các lớp, đảm bảo mỗi lớp có trọng số ngang nhau.
- **Precision:** Độ chính xác của các dự đoán thuộc từng lớp.
- **Recall:** Khả năng nhận diện đúng các mẫu thuộc từng lớp.
- **Confusion Matrix:** Ma trận thể hiện các trường hợp dự đoán đúng và nhầm lẫn giữa các lớp.
- **Error Analysis:** Phân tích những hình ảnh được mô hình dự đoán sai.

## 11. Hạn chế và hướng phát triển

### Hạn chế

- Hệ thống hiện chỉ hỗ trợ 10 lớp món ăn đã được huấn luyện.
- Kết quả nhận dạng có thể bị ảnh hưởng bởi chất lượng hình ảnh, ánh sáng và góc chụp.
- Một số món ăn có hình thức tương đồng có thể gây nhầm lẫn cho mô hình.

### Hướng phát triển

- Mở rộng số lượng lớp món ăn.
- Bổ sung dữ liệu hình ảnh thực tế.
- Thử nghiệm các kiến trúc Deep Learning khác.
- Cải thiện khả năng nhận dạng đối với những lớp có đặc điểm hình ảnh tương đồng.
- Triển khai ứng dụng trên nền tảng trực tuyến.

## 12. Thông tin dự án

**Tên dự án:** FoodVision AI

**Lĩnh vực:** Deep Learning – Computer Vision

**Bộ dữ liệu:** Food-101 (10 lớp được lựa chọn)

**Mô hình sử dụng:** CNN Baseline, ResNet18 Frozen, ResNet18 Fine-tuning

**Giao diện:** Streamlit

**Mục đích:** Học tập và nghiên cứu trong khuôn khổ môn Deep Learning.
