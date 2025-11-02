# BƯỚC 5: TẠO CONTENT ITEMS QUA ADMIN PANEL

## Mục tiêu
Tạo các Content Items thực tế để lưu trữ dữ liệu Footer, có thể chỉnh sửa qua Admin Panel.

## Kiến thức cần biết
- **Content Item**: Dữ liệu thực tế được tạo từ Content Type
- **Widget Content Item**: Content Item có Stereotype = Widget
- **Admin Panel**: Giao diện quản trị để tạo/sửa Content Items
- **Display Text Pattern**: Cấu hình hiển thị tên Content Item trong danh sách

## ⚠️ VẤN ĐỀ CẦN GIẢI QUYẾT TRƯỚC
Khi tạo nhiều Content Items cùng loại (như FooterSocial), chúng sẽ hiển thị tên giống nhau trong Admin Panel, gây khó khăn trong quản lý. Cần cấu hình **Display Text Pattern** để phân biệt.

## Content Items cần tạo

### 1. Footer Contact Item (Thông tin liên hệ)
### 2. Footer Social Items (Các mạng xã hội)
### 3. Footer About Item (Giới thiệu)

## Các bước thực hiện

### BƯỚC 5.0: Cấu hình Display Text Pattern (Bắt buộc)

#### 1. Cấu hình FooterSocial Content Type
- Vào **Content Definition → Content Types**
- Click **Edit** trên **FooterSocial**
- Tìm phần **Display Text** (ở cuối form)
- Nhập pattern: `{{ ContentItem.Content.FooterSocial.SocialName.Text }}`
- Click **Save**

#### 2. Cấu hình FooterContact Content Type  
- Click **Edit** trên **FooterContact**
- Nhập Display Text pattern: `{{ ContentItem.Content.FooterContact.CompanyName.Text }}`
- Click **Save**

#### 3. Cấu hình FooterAbout Content Type
- Click **Edit** trên **FooterAbout** 
- Nhập Display Text pattern: `{{ ContentItem.Content.FooterAbout.Title.Text }}`
- Click **Save**

> **Lưu ý**: Sau khi cấu hình, Content Items sẽ hiển thị tên theo nội dung field thay vì tên Content Type.

### BƯỚC 5.1: Tạo Footer Contact Item

#### 1. Truy cập Admin Panel
- Vào **Content → Content Items**
- Click **New** → Chọn **FooterContact**

#### 2. Điền thông tin các fields
```
Fields:
├── CompanyName: "Công Ty TNHH ABC Technology"
├── Address: "123 Đường Nguyễn Văn Linh, Quận 7, TP.HCM"
├── Phone: "+84 28 1234 5678"
└── Email: "contact@abctech.com"
```

#### 3. Publish Content Item
- Click **Publish** để xuất bản
- Kiểm tra trạng thái: **Published**
- **Tên hiển thị**: Sẽ là "Công Ty TNHH ABC Technology" (theo Display Text Pattern)

### BƯỚC 5.2: Tạo Footer Social Items

#### 1. Tạo Facebook Social Item
- Click **New** → Chọn **FooterSocial**
```
Fields:
├── SocialName: "Facebook"
├── SocialUrl: "https://facebook.com/abctech"
└── SocialIcon: "fab fa-facebook"
```
- Click **Publish**
- **Tên hiển thị**: Sẽ là "Facebook" (theo Display Text Pattern)

#### 2. Tạo Twitter Social Item
- Click **New** → Chọn **FooterSocial**
```
Fields:
├── SocialName: "Twitter"
├── SocialUrl: "https://twitter.com/abctech"
└── SocialIcon: "fab fa-twitter"
```
- Click **Publish**
- **Tên hiển thị**: Sẽ là "Twitter"

#### 3. Tạo Instagram Social Item
- Click **New** → Chọn **FooterSocial**
```
Fields:
├── SocialName: "Instagram"
├── SocialUrl: "https://instagram.com/abctech"
└── SocialIcon: "fab fa-instagram"
```
- Click **Publish**
- **Tên hiển thị**: Sẽ là "Instagram"

#### 4. Tạo LinkedIn Social Item
- Click **New** → Chọn **FooterSocial**
```
Fields:
├── SocialName: "LinkedIn"
├── SocialUrl: "https://linkedin.com/company/abctech"
└── SocialIcon: "fab fa-linkedin"
```
- Click **Publish**
- **Tên hiển thị**: Sẽ là "LinkedIn"

### BƯỚC 5.3: Tạo Footer About Item

#### 1. Tạo About Content Item
- Click **New** → Chọn **FooterAbout**
```
Fields:
├── Title: "Về Công Ty Chúng Tôi"
└── Description: 
    "ABC Technology là công ty hàng đầu chuyên về các giải pháp phần mềm sáng tạo. 
    Với hơn 10 năm kinh nghiệm, chúng tôi giúp các doanh nghiệp chuyển đổi số và 
    đạt được mục tiêu thông qua công nghệ tiên tiến và dịch vụ xuất sắc."
```
- Click **Publish**
- **Tên hiển thị**: Sẽ là "Về Công Ty Chúng Tôi" (theo Display Text Pattern)

## Kiểm tra Content Items đã tạo

### 1. Danh sách Content Items
Vào **Content → Content Items**, kiểm tra:

```
✅ Công Ty TNHH ABC Technology (FooterContact) - Published
✅ Facebook (FooterSocial) - Published  
✅ Twitter (FooterSocial) - Published
✅ Instagram (FooterSocial) - Published
✅ LinkedIn (FooterSocial) - Published
✅ Về Công Ty Chúng Tôi (FooterAbout) - Published
```

> **Lưu ý**: Nhờ Display Text Pattern (đã sửa với `.Content.`), mỗi Content Item hiển thị tên riêng biệt thay vì tên Content Type, giúp dễ dàng quản lý.

### ⚠️ Vấn đề Display Text Pattern đã giải quyết
- **Vấn đề ban đầu**: Pattern thiếu `.Content.` → hiển thị tên Content Type
- **Giải pháp**: Thêm `.Content.` vào pattern → hiển thị đúng field value
- **Kết quả**: Tất cả Content Items hiển thị tên chính xác ✅

### 2. Kiểm tra dữ liệu
Click **Edit** từng Content Item để xác nhận:
- Tất cả fields đã được điền đầy đủ
- Trạng thái là **Published**
- Không có lỗi validation

## Test hiển thị Content Items

### 1. Tạo Widget test (tạm thời)
- Vào **Design → Widgets**
- Chọn zone **Footer**
- Click **Add Widget** → Chọn **Footer Contact**
- Chọn Content Item: **Công Ty TNHH ABC Technology**
- Save và xem kết quả trên frontend

### 2. Kiểm tra template
- Mở trang web để xem Footer
- Kiểm tra template hiển thị đúng dữ liệu
- Kiểm tra responsive trên mobile

## Quản trị Content Items

### 1. Chỉnh sửa thông tin
```
Để thay đổi thông tin Footer:
1. Vào Content → Content Items
2. Tìm Content Item cần sửa
3. Click Edit
4. Thay đổi thông tin
5. Click Save → Publish
6. Thông tin tự động cập nhật trên website
```

### 2. Thêm Content Item mới
```
Để thêm mạng xã hội mới:
1. Content → Content Items → Create New
2. Chọn Footer Social
3. Điền thông tin (YouTube, TikTok...)
4. Publish
5. Gán vào Widget trong Layers
```

## Kết quả mong đợi
- 6 Content Items được tạo thành công ✅
- Tất cả đều ở trạng thái Published ✅
- Display Text Pattern hoạt động hoàn hảo ✅
- Dữ liệu hiển thị đúng trên frontend ✅
- Có thể chỉnh sửa qua Admin Panel ✅
- **Đã cleanup test data** (xóa các test items) ✅

## Bước tiếp theo
→ **BƯỚC 6**: Setup Layers và gán Widgets vào Footer Zone

## Ghi chú quan trọng
- **Content Items** chứa dữ liệu thực tế
- **Admin Panel** cho phép chỉnh sửa dễ dàng
- Thay đổi Content Item sẽ tự động cập nhật trên website
- Có thể tạo nhiều Content Items cho cùng 1 Content Type
- **Display Text Pattern** phải có `.Content.` để hoạt động đúng
- **Re-publish** Content Items sau khi sửa Display Text Pattern
- **Cleanup test data** để giữ dự án sạch sẽ và professional