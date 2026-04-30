# Bảng Phân Chia Công Việc - Dự án Smart Parking (Nhóm 6 Thành viên)

Dưới đây là danh sách chi tiết các file cụ thể mà mỗi thành viên sẽ trực tiếp tương tác, chỉnh sửa và chịu trách nhiệm chính.

| Thành viên | Vai trò chính | Các file cụ thể cần tương tác | Công việc cụ thể |
| :--- | :--- | :--- | :--- |
| **Thành viên 1** (Trưởng nhóm) | **Kiến trúc & Tài liệu** | - `backend/core_cv/pipeline.py`<br>- `README.md`<br>- `docs/Work_Division.md`<br>- `docs/Báo_cáo_Final.pdf` | - Kết nối các module CV vào một luồng duy nhất.<br>- Viết báo cáo và tài liệu hướng dẫn hệ thống. |
| **Thành viên 2** | **Tiền xử lý & Phân đoạn** | - `backend/core_cv/preprocessing.py`<br>- `backend/core_cv/segmentation.py` | - Xử lý ảnh (CLAHE, Blur, Grayscale).<br>- Thuật toán phân đoạn vùng ô đỗ xe (Variance). |
| **Thành viên 3** | **Đặc trưng & Nhận dạng** | - `backend/core_cv/feature_extraction.py`<br>- `backend/core_cv/train_svm.py`<br>- `backend/models/svm_parking_model.xml` | - Trích xuất đặc trưng HOG.<br>- Huấn luyện và xuất file mô hình SVM (`.xml`). |
| **Thành viên 4** | **Kỹ sư Dữ liệu & Đánh giá** | - `backend/extract_frames.py`<br>- `backend/data/train/ (occupied, empty)`<br>- `notebooks/*.ipynb` (00, 01, 02) | - Cắt ảnh từ video, gán nhãn dữ liệu.<br>- Chạy thực nghiệm, đánh giá độ chính xác (Recall/Precision). |
| **Thành viên 5** | **Phát triển Backend** | - `backend/main.py`<br>- `backend/requirements.txt`<br>- `backend/models/parking_spots.json` | - Xây dựng API FastAPI và WebSocket Server.<br>- Lưu trữ/Quản lý tọa độ các ô đỗ xe vào file JSON. |
| **Thành viên 6** | **Phát triển Frontend** | - `frontend/src/App.vue`<br>- `frontend/src/components/BoundingBox.vue`<br>- `frontend/src/components/VideoManager.vue`<br>- `frontend/src/services/socketClient.js` | - Xây dựng giao diện điều khiển và sơ đồ bãi xe.<br>- Code chức năng vẽ Bounding Box và kết nối WebSocket. |

---

## Chi tiết nhiệm vụ và các File tương ứng

### 1. Thành viên 1: Trưởng nhóm & Kiến trúc sư
*   **File chính:** `backend/core_cv/pipeline.py`
    *   *Nhiệm vụ:* Import các hàm từ `preprocessing`, `segmentation`, `feature_extraction` để tạo ra function `process_frame()` hoàn chỉnh cho Backend gọi vào.
*   **Tài liệu:** `README.md`, `Work_Division.md`. Đảm bảo sơ đồ kiến trúc hệ thống khớp với thực tế code.

### 2. Thành viên 2: Kỹ sư Tiền xử lý
*   **File chính:** `backend/core_cv/preprocessing.py`
    *   *Nhiệm vụ:* Viết hàm `apply_preprocessing(image)` để làm sạch ảnh, giảm nhiễu trước khi đưa vào nhận dạng.
*   **File phụ:** `backend/core_cv/segmentation.py`
    *   *Nhiệm vụ:* Triển khai hàm tính `variance` để lọc các ô trống mà không cần chạy AI, giúp tăng hiệu năng.

### 3. Thành viên 3: Chuyên gia Nhận dạng
*   **File code:** `backend/core_cv/feature_extraction.py`, `backend/core_cv/train_svm.py`
    *   *Nhiệm vụ:* Cấu hình các tham số HOG (pixels per cell, cells per block). Viết script huấn luyện SVM.
*   **File output:** `backend/models/svm_parking_model.xml`
    *   *Nhiệm vụ:* Đây là "trái tim" của hệ thống, thành viên 3 chịu trách nhiệm độ chính xác của file này.

### 4. Thành viên 4: Kỹ sư Dữ liệu & Kiểm thử
*   **File chính:** `backend/extract_frames.py`
    *   *Nhiệm vụ:* Viết script giúp các thành viên khác dễ dàng cắt dữ liệu từ video mới để mở rộng tập dataset.
*   **Dữ liệu:** Quản lý thư mục `backend/data/`. Đảm bảo dữ liệu không bị nhầm lẫn giữa hai lớp "có xe" và "không xe".
*   **Phân tích:** Các file Notebook trong `notebooks/` để vẽ biểu đồ loss/accuracy.

### 5. Thành viên 5: Lập trình viên Backend
*   **File chính:** `backend/main.py`
    *   *Nhiệm vụ:* Setup FastAPI app, định nghĩa các route `@app.get("/status")` và xử lý `@app.websocket("/ws")`.
*   **Quản lý cấu hình:** `backend/models/parking_spots.json`
    *   *Nhiệm vụ:* Khi người dùng vẽ ô đỗ xe trên Web, Backend nhận tọa độ và ghi vào file này để hệ thống ghi nhớ sau khi khởi động lại.

### 6. Thành viên 6: Lập trình viên Frontend
*   **Layout chính:** `frontend/src/App.vue`
    *   *Nhiệm vụ:* Bố cục tổng thể của Dashboard (Video bên trái, Bảng điều khiển bên phải).
*   **Components:** 
    *   `BoundingBox.vue`: Logic cho phép dùng chuột vẽ hình chữ nhật lên màn hình.
    *   `VideoManager.vue`: Xử lý việc hiển thị canvas stream từ Backend.
*   **Kết nối:** `frontend/src/services/socketClient.js`
    *   *Nhiệm vụ:* Viết logic gửi/nhận dữ liệu JSON qua WebSocket để cập nhật trạng thái ô đỗ xe thời gian thực.
