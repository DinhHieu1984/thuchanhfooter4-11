# 🚀 HƯỚNG DẪN SETUP DATABASE CHO FOOTER 3 CỘT

## ⚠️ VẤN ĐỀ: Footer không hiển thị dữ liệu khi tải code về máy mới

### 🔍 NGUYÊN NHÂN:
- Database SQLite (`OrchardCore.db`) chứa tất cả dữ liệu widgets
- Mỗi máy cần setup riêng database và tạo lại widgets

### 🛠️ GIẢI PHÁP:

## BƯỚC 1: Chạy ứng dụng lần đầu
```bash
cd FooterThucHanh
dotnet run --urls=http://localhost:5000
```

## BƯỚC 2: Setup OrchardCore (lần đầu chạy)
1. Truy cập: `http://localhost:5000`
2. Chọn **"Blog"** recipe
3. Tạo admin account
4. Hoàn thành setup

## BƯỚC 3: Tạo lại Footer Widgets
### 3.1. Tạo Content Types (nếu chưa có):
- Vào **Admin → Content → Content Types**
- Tạo 3 Content Types:
  - `FooterSocial` (HTML Body Field)
  - `FooterAbout` (HTML Body Field) 
  - `FooterContact` (HTML Body Field)

### 3.2. Tạo Widget Templates:
- Vào **Admin → Design → Templates**
- Tạo 3 templates:
  - `Widget-FooterSocial.liquid`
  - `Widget-FooterAbout.liquid`
  - `Widget-FooterContact.liquid`

### 3.3. Tạo Widgets và gán vào Zones:
- Vào **Admin → Design → Widgets**
- Tạo widgets cho từng zone:
  - `FooterLeft` (FooterSocial)
  - `FooterCenter` (FooterAbout)
  - `FooterRight` (FooterContact)

## BƯỚC 4: Copy nội dung từ hướng dẫn
- Làm theo file `4.HUONG_DAN_TAO_3_WIDGETS.md`
- Copy đúng HTML content cho từng widget
- Đảm bảo CSS classes được áp dụng đúng

## 🎯 KẾT QUẢ MONG MUỐN:
Footer sẽ hiển thị 3 cột màu sắc:
- **Cột 1 (Xanh dương)**: Kết Nối Với Chúng Tôi
- **Cột 2 (Xanh lá)**: Giờ Làm Việc  
- **Cột 3 (Xanh cyan)**: Liên Hệ Chúng Tôi

## 📞 HỖ TRỢ:
Nếu gặp khó khăn, hãy làm theo từng bước trong thư mục `HuongdanFooter/`