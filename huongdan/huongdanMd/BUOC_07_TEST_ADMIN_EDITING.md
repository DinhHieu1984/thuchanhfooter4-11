# BƯỚC 7: TEST VÀ QUẢN TRỊ FOOTER ĐỘNG

## Mục tiêu
Test đầy đủ chức năng Footer động và hướng dẫn quản trị thông qua Admin Panel.

## Kiến thức cần biết
- **Dynamic Content**: Nội dung có thể thay đổi qua Admin Panel
- **Live Updates**: Thay đổi hiển thị ngay lập tức
- **Content Management**: Quản lý nội dung không cần code

## Các test cases cần thực hiện

### 1. Test hiển thị Footer
### 2. Test chỉnh sửa qua Admin Panel
### 3. Test responsive design
### 4. Test performance

## Các bước thực hiện

### BƯỚC 7.1: Test Hiển Thị Footer

#### 1. Test trên các trang khác nhau
```
✅ Trang chủ (Homepage): Footer hiển thị đầy đủ
✅ Trang About: Footer hiển thị đầy đủ
✅ Trang Blog: Footer hiển thị đầy đủ
✅ Trang Contact: Footer hiển thị đầy đủ
✅ Trang 404: Footer hiển thị đầy đủ
```

#### 2. Test nội dung hiển thị
```
Contact Section:
├── ✅ Company Name hiển thị
├── ✅ Address hiển thị với icon
├── ✅ Phone có link tel: hoạt động
└── ✅ Email có link mailto: hoạt động

About Section:
├── ✅ Title hiển thị
└── ✅ HTML content render đúng

Social Section:
├── ✅ Facebook link hoạt động, mở tab mới
├── ✅ Twitter link hoạt động, mở tab mới
├── ✅ Instagram link hoạt động, mở tab mới
└── ✅ LinkedIn link hoạt động, mở tab mới
```

#### 3. Test responsive design
```
Desktop (>1200px): ✅ 3 cột hiển thị ngang
Tablet (768-1199px): ✅ 3 cột responsive
Mobile (<768px): ✅ 1 cột xếp dọc, center align
```

### BƯỚC 7.2: Test Chỉnh Sửa Qua Admin Panel

#### 1. Test thay đổi thông tin liên hệ
```
Bước test:
1. Vào Content → Content Items
2. Edit "Thông Tin Liên Hệ Công Ty"
3. Thay đổi số điện thoại: "+84 28 9999 8888"
4. Save → Publish
5. Refresh trang web
6. ✅ Kiểm tra số điện thoại đã thay đổi
```

#### 2. Test thêm mạng xã hội mới
```
Bước test:
1. Content → Content Items → Create New
2. Chọn Footer Social
3. Điền thông tin:
   - Platform Name: "YouTube"
   - Social URL: "https://youtube.com/@yourcompany"
   - Icon Class: "fab fa-youtube"
4. Publish
5. Design → Widgets → Default Layer → Footer
6. Add Widget → Footer Social → Chọn YouTube item
7. Position: 7
8. Save
9. ✅ Kiểm tra YouTube link xuất hiện trong Footer
```

#### 3. Test chỉnh sửa nội dung About
```
Bước test:
1. Edit "Giới Thiệu Công Ty" Content Item
2. Thay đổi About Content, thêm:
   "<p><strong>Giá trị cốt lõi:</strong> Chất lượng - Uy tín - Đổi mới</p>"
3. Save → Publish
4. ✅ Kiểm tra nội dung mới hiển thị trong Footer
```

### BƯỚC 7.3: Test Quản Lý Widgets

#### 1. Test thay đổi thứ tự hiển thị
```
Bước test:
1. Design → Widgets → Default Layer
2. Trong Footer Zone, kéo About Widget lên Position 1
3. Save
4. ✅ Kiểm tra About hiển thị đầu tiên
```

#### 2. Test ẩn/hiện Widget
```
Bước test:
1. Edit một Social Widget
2. Uncheck "Published"
3. Save
4. ✅ Kiểm tra Widget không hiển thị trên Frontend
5. Check "Published" lại
6. ✅ Kiểm tra Widget hiển thị trở lại
```

#### 3. Test xóa Widget
```
Bước test:
1. Delete một Social Widget
2. ✅ Kiểm tra Widget biến mất khỏi Footer
3. Tạo lại Widget nếu cần
```

### BƯỚC 7.4: Test Performance

#### 1. Test tốc độ tải trang
```
Tools: Chrome DevTools → Network
✅ Footer không làm chậm tốc độ tải trang
✅ CSS/JS load nhanh
✅ Images (nếu có) được optimize
```

#### 2. Test caching
```
✅ Content thay đổi hiển thị ngay (no cache issues)
✅ Static assets (CSS/JS) được cache
```

### BƯỚC 7.5: Test Accessibility

#### 1. Test keyboard navigation
```
✅ Tab qua các links trong Footer
✅ Enter/Space kích hoạt links
✅ Focus visible rõ ràng
```

#### 2. Test screen reader
```
✅ Alt text cho icons
✅ Semantic HTML structure
✅ ARIA labels nếu cần
```

## Hướng dẫn quản trị cho End User

### 1. Thay đổi thông tin liên hệ
```
📋 HƯỚNG DẪN CHO ADMIN:

Để thay đổi thông tin công ty trong Footer:
1. Đăng nhập Admin Panel
2. Vào Content → Content Items
3. Tìm "Thông Tin Liên Hệ Công Ty"
4. Click Edit
5. Thay đổi thông tin cần thiết
6. Click Save → Publish
7. Thông tin tự động cập nhật trên website

⚠️ Lưu ý: Phải click Publish để thay đổi có hiệu lực
```

### 2. Thêm/sửa mạng xã hội
```
📋 THÊM MẠNG XÃ HỘI MỚI:

1. Content → Content Items → Create New
2. Chọn "Footer Social"
3. Điền thông tin:
   - Platform Name: Tên mạng xã hội
   - Social URL: Link đầy đủ
   - Icon Class: Mã icon Font Awesome
4. Publish
5. Design → Widgets → Default Layer
6. Trong Footer Zone, click Add Widget
7. Chọn Footer Social → Chọn item vừa tạo
8. Save

📋 ICON CLASSES THÔNG DỤNG:
- Facebook: "fab fa-facebook-f"
- Twitter: "fab fa-twitter"
- Instagram: "fab fa-instagram"
- LinkedIn: "fab fa-linkedin-in"
- YouTube: "fab fa-youtube"
- TikTok: "fab fa-tiktok"
```

### 3. Chỉnh sửa nội dung giới thiệu
```
📋 SỬA NỘI DUNG GIỚI THIỆU:

1. Content → Content Items
2. Edit "Giới Thiệu Công Ty"
3. Thay đổi About Title và About Content
4. Sử dụng editor để format text (bold, italic, links)
5. Save → Publish

💡 Tips: Có thể sử dụng HTML tags trong About Content
```

## Troubleshooting

### 1. Footer không hiển thị
```
❌ Vấn đề: Footer trống hoặc không hiển thị

✅ Giải pháp:
1. Kiểm tra Theme đã set Default chưa
2. Kiểm tra Layout.liquid có Footer Zone chưa
3. Kiểm tra Widgets đã được gán vào Footer Zone chưa
4. Kiểm tra Content Items đã Published chưa
```

### 2. Template không hiển thị đúng
```
❌ Vấn đề: Widget hiển thị sai format

✅ Giải pháp:
1. Kiểm tra file Widget-[ContentType].liquid
2. Kiểm tra CSS trong site.css
3. Clear cache: Configuration → Performance → Clear Cache
```

### 3. Links không hoạt động
```
❌ Vấn đề: Social links không click được

✅ Giải pháp:
1. Kiểm tra URL có đầy đủ http:// hoặc https://
2. Kiểm tra target="_blank" trong template
3. Test link trực tiếp trong browser
```

## Kết quả mong đợi
- ✅ Footer hiển thị đúng trên tất cả trang
- ✅ Responsive hoàn hảo trên mọi thiết bị
- ✅ Admin có thể chỉnh sửa dễ dàng
- ✅ Performance tốt, không ảnh hưởng tốc độ
- ✅ Accessibility đạt chuẩn

## Bước tiếp theo
→ **BƯỚC 8**: Tối ưu hóa và mở rộng tính năng

## Ghi chú quan trọng
- **Footer động** = có thể chỉnh sửa qua Admin Panel
- **OrchardCore CMS** cung cấp đầy đủ công cụ quản trị
- **End User** không cần biết code để quản lý nội dung
- **Scalable**: Dễ dàng thêm Content Types và Widgets mới