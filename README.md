# Smart_parking

Smart_parking là hệ thống quản lý bãi đỗ xe thông minh sử dụng Computer Vision để nhận diện và giám sát trạng thái các vị trí đỗ xe theo thời gian thực.

## Mục lục
- [Giới thiệu](#giới-thiệu)
- [Cấu trúc dự án](#cấu-trúc-dự-án)
- [Cài đặt & Chạy thử](#cài-đặt--chạy-thử)
- [Công nghệ sử dụng](#công-nghệ-sử-dụng)
- [Liên hệ](#liên-hệ)

## Giới thiệu

Dự án gồm 2 phần chính:
- **Backend**: Xử lý ảnh/video, nhận diện vị trí đỗ xe, cung cấp API và WebSocket.
- **Frontend**: Giao diện web hiển thị trạng thái bãi đỗ xe theo thời gian thực.

## Cấu trúc dự án

```
Smart_parking/
│
├── backend/           # Xử lý CV, API, quản lý camera, mô hình ML
│   ├── api/           # Định nghĩa API và WebSocket
│   ├── core_cv/       # Xử lý ảnh, trích xuất đặc trưng, train SVM
│   ├── models/        # File mô hình, cấu hình vị trí đỗ xe
│   ├── services/      # Quản lý camera, bãi đỗ xe
│   ├── tests/         # Script đánh giá mô hình
│   ├── main.py        # Điểm khởi động backend
│   └── requirements.txt
│
├── frontend/          # Ứng dụng web (Vue.js + Vite)
│   ├── public/
│   ├── src/
│   │   ├── components/    # Các component Vue
│   │   ├── services/      # Kết nối WebSocket
│   │   ├── App.vue, main.js, style.css
│   ├── package.json
│   └── vite.config.js
│
└── README.md          # Tài liệu này
```

## Cài đặt & Chạy thử

### Backend (Python)
1. Cài đặt Python 3.8+
2. Cài các thư viện cần thiết:
	```
	pip install -r backend/requirements.txt
	```
3. Chạy backend:
	```
	python backend/main.py
	```

### Frontend (Vue.js)
1. Cài Node.js >= 16
2. Cài dependencies:
	```
	cd frontend
	npm install
	```
3. Chạy ứng dụng:
	```
	npm run dev
	```

## Công nghệ sử dụng

- **Backend**: Python, OpenCV, scikit-learn, FastAPI (hoặc Flask), WebSocket
- **Frontend**: Vue.js, Vite, JavaScript

