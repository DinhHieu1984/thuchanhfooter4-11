# BƯỚC 3: TẠO CONTENT TYPES CHO FOOTER

## Mục tiêu
Tạo các Content Types để lưu trữ thông tin Footer có thể quản trị qua Admin Panel.

## Kiến thức cần biết
- **Content Type**: Định nghĩa cấu trúc dữ liệu
- **Content Field**: Các trường dữ liệu (Text, HTML, Link...)
- **Stereotype**: Phân loại Content Type (Widget, Content...)

## Các Content Types cần tạo

### 1. FooterContact (Thông tin liên hệ)
### 2. FooterSocial (Mạng xã hội)
### 3. FooterAbout (Giới thiệu)

## Các bước thực hiện

### BƯỚC 3.1: Tạo FooterContact Content Type

#### 1. Vào Admin Panel
- Truy cập: **Content → Content Types**
- Click **Create new type**

#### 2. Cấu hình cơ bản
```
Name: FooterContact
Display Name: Footer Contact
Description: Thông tin liên hệ trong Footer
Stereotype: Widget (QUAN TRỌNG)
```

#### 3. Thêm các Fields
**a) Company Name Field**
```
Field Type: Text Field
Technical Name: CompanyName
Display Name: Tên Công Ty
Settings:
  - Required: Yes
  - Placeholder: "Nhập tên công ty"
```

**b) Address Field**
```
Field Type: Text Field
Technical Name: Address
Display Name: Địa Chỉ
Settings:
  - Required: Yes
  - Placeholder: "Nhập địa chỉ"
```

**c) Phone Field**
```
Field Type: Text Field
Technical Name: Phone
Display Name: Số Điện Thoại
Settings:
  - Required: Yes
  - Placeholder: "+84 xxx xxx xxx"
```

**d) Email Field**
```
Field Type: Text Field
Technical Name: Email
Display Name: Email
Settings:
  - Required: Yes
  - Placeholder: "contact@company.com"
```

### BƯỚC 3.2: Tạo FooterSocial Content Type

#### 1. Tạo Content Type mới
```
Name: FooterSocial
Display Name: Footer Social
Description: Liên kết mạng xã hội trong Footer
Stereotype: Widget
```

#### 2. Thêm các Fields
**a) Platform Name Field**
```
Field Type: Text Field
Technical Name: PlatformName
Display Name: Tên Nền Tảng
Settings:
  - Required: Yes
  - Placeholder: "Facebook, Twitter, Instagram..."
```

**b) Social URL Field**
```
Field Type: Link Field
Technical Name: SocialUrl
Display Name: Đường Dẫn
Settings:
  - Required: Yes
  - Link Text: Optional
  - Target: _blank
```

**c) Icon Class Field**
```
Field Type: Text Field
Technical Name: IconClass
Display Name: Icon Class
Settings:
  - Required: Yes
  - Placeholder: "fab fa-facebook-f"
  - Hint: "Font Awesome icon class"
```

### BƯỚC 3.3: Tạo FooterAbout Content Type

#### 1. Tạo Content Type mới
```
Name: FooterAbout
Display Name: Footer About
Description: Thông tin giới thiệu trong Footer
Stereotype: Widget
```

#### 2. Thêm các Fields
**a) About Title Field**
```
Field Type: Text Field
Technical Name: AboutTitle
Display Name: Tiêu Đề
Settings:
  - Required: Yes
  - Placeholder: "Về Chúng Tôi"
```

**b) About Content Field**
```
Field Type: HTML Field
Technical Name: AboutContent
Display Name: Nội Dung
Settings:
  - Required: Yes
  - Editor: Trumbowyg
  - Allow HTML: Yes
```

## Kiểm tra kết quả

### 1. Xác nhận Content Types đã tạo
Vào **Content → Content Types**, kiểm tra:
- ✅ FooterContact (Stereotype: Widget)
- ✅ FooterSocial (Stereotype: Widget)  
- ✅ FooterAbout (Stereotype: Widget)

### 2. Kiểm tra trong Widgets
Vào **Design → Widgets**, trong danh sách **Add Widget** phải thấy:
- ✅ Footer Contact
- ✅ Footer Social
- ✅ Footer About

## Kết quả mong đợi
- 3 Content Types được tạo thành công
- Tất cả đều có Stereotype = Widget
- Xuất hiện trong danh sách Add Widget

## Bước tiếp theo
→ **BƯỚC 4**: Tạo Widget Templates để hiển thị Content Types

## Ghi chú quan trọng
- **Stereotype: Widget** là bắt buộc để Content Type xuất hiện trong Widgets
- Các Fields được thiết kế để dễ quản trị qua Admin Panel
- Link Field tự động tạo thẻ `<a>` với target="_blank"