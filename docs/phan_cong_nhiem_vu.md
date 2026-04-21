# 📌 Bảng phân công công việc – Smart Parking

| Thành viên   | Vai trò                            | Phần phụ trách                      | Công việc chi tiết |
|--------------|------------------------------------|-------------------------------------|--------------------|
| **Member 1** | 🔥 Backend Lead + API              | `backend/api/`, `main.py`           | - Thiết kế REST API (lấy trạng thái bãi xe, camera)<br>- Xây dựng WebSocket realtime<br>- Tạo endpoint: `/parking-status`, `/camera-stream`<br>- Kết nối với service layer<br>- Quản lý lifecycle backend (start/stop server)<br>- Validate dữ liệu trả về |
| **Member 2** | 🎥 Computer Vision Engineer        | `backend/core_cv/`                  | - Xử lý ảnh/video bằng OpenCV<br>- Viết logic detect vị trí đỗ xe<br>- Trích xuất feature (HOG/SIFT hoặc custom)<br>- Train model SVM<br>- Tối ưu độ chính xác nhận diện<br>- Xây pipeline: camera → trạng thái slot |
| **Member 3** | 🧠 Model + Data Engineer           | `backend/models/`, `backend/tests/` | - Quản lý dataset (ảnh bãi xe)<br>- Tạo file config vị trí parking slot<br>- Lưu/Load model SVM<br>- Viết script test accuracy<br>- Đánh giá model (precision, recall)<br>- Tối ưu model size và tốc độ |
| **Member 4** | ⚙️ Backend Services                | `backend/services/`                 | - Quản lý camera (connect, disconnect)<br>- Viết logic mapping camera → parking slots<br>- Xử lý luồng dữ liệu realtime<br>- Đồng bộ dữ liệu giữa CV và API<br>- Cache trạng thái bãi xe<br>- Xử lý lỗi camera |
| **Member 5** | 🎨 Frontend Dev (UI + Components)  | `frontend/src/components/`          | - Thiết kế UI hiển thị bãi đỗ xe<br>- Vẽ layout parking slot (grid/map)<br>- Tạo component hiển thị trạng thái (trống/đầy)<br>- Responsive UI<br>- Thêm animation trạng thái slot<br>- Tối ưu UX |
| **Member 6** | 🔌 Frontend + Realtime Integration | `frontend/src/services/`            | - Kết nối WebSocket với backend<br>- Nhận dữ liệu realtime<br>- Update UI theo trạng thái mới<br>- Xử lý reconnect khi mất kết nối<br>- Tối ưu performance (debounce/throttle)<br>- Debug data flow frontend ↔ backend |

---

## 🎯 Ghi chú

- Tất cả thành viên đều phải **tham gia code**
- Không có vai trò chỉ viết báo cáo
- Mỗi phần phải chạy độc lập trước khi tích hợp
- Hệ thống cuối cùng phải chạy end-to-end (backend + frontend + realtime)

---