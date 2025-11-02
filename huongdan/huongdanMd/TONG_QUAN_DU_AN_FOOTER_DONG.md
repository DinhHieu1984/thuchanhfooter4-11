# HƯỚNG DẪN XÂY DỰNG FOOTER ĐỘNG VỚI ORCHARDCORE CMS

> 📋 **Tài liệu này**: Tổng quan chi tiết về dự án Footer động OrchardCore CMS  
> 🚀 **Bắt đầu nhanh**: Xem [README.md](README.md) để có mục lục đầy đủ các bước thực hiện

## Tổng quan dự án

Dự án này hướng dẫn xây dựng **Footer động** cho website sử dụng **OrchardCore CMS**, cho phép quản trị viên dễ dàng chỉnh sửa nội dung Footer qua Admin Panel mà không cần code.

## Kiến trúc OrchardCore CMS

```
OrchardCore Architecture:
├── Layout (định nghĩa cấu trúc trang)
├── Zones (vùng hiển thị: Header, Footer, Sidebar...)
├── Content Types (cấu trúc dữ liệu)
├── Content Items (dữ liệu thực tế)
├── Widgets (thành phần hiển thị)
├── Layers (quy tắc hiển thị)
└── Admin Panel (giao diện quản trị)
```

## Tính năng chính

### ✅ Footer động hoàn toàn
- Thông tin liên hệ (công ty, địa chỉ, điện thoại, email)
- Liên kết mạng xã hội (Facebook, Twitter, Instagram, LinkedIn)
- Nội dung giới thiệu (HTML editor)
- Responsive design (Bootstrap 5)

### ✅ Quản trị qua Admin Panel
- Tạo/sửa/xóa nội dung không cần code
- Live preview khi chỉnh sửa
- Workflow approval (nếu cần)
- Multi-user management

### ✅ Hiệu suất cao
- Caching tự động
- Lazy loading
- Minified CSS/JS
- SEO-friendly

## Cấu trúc hướng dẫn

### 📚 8 Bước thực hiện chi tiết

| Bước | Tên file | Mô tả | Thời gian |
|------|----------|-------|-----------|
| 1 | [BUOC_01_TAO_DU_AN_ORCHARDCORE.md](BUOC_01_TAO_DU_AN_ORCHARDCORE.md) | Tạo dự án OrchardCore CMS chuẩn | 30 phút |
| 2 | [BUOC_02_TAO_LAYOUT_ZONES.md](BUOC_02_TAO_LAYOUT_ZONES.md) | Tạo Layout với Zones (Footer Zone) | 45 phút |
| 3 | [BUOC_03_TAO_CONTENT_TYPES.md](BUOC_03_TAO_CONTENT_TYPES.md) | Tạo Content Types cho Footer | 60 phút |
| 4 | [BUOC_04_TAO_WIDGET_TEMPLATES.md](BUOC_04_TAO_WIDGET_TEMPLATES.md) | Tạo Widget Templates (Liquid) | 90 phút |
| 5 | [BUOC_05_TAO_CONTENT_ITEMS.md](BUOC_05_TAO_CONTENT_ITEMS.md) | Tạo Content Items qua Admin Panel | 30 phút |
| 6 | [BUOC_06_SETUP_LAYERS_WIDGETS.md](BUOC_06_SETUP_LAYERS_WIDGETS.md) | Setup Layers và gán Widgets | 45 phút |
| 7 | [BUOC_07_TEST_ADMIN_EDITING.md](BUOC_07_TEST_ADMIN_EDITING.md) | Test và quản trị Footer động | 60 phút |
| 8 | [BUOC_08_TOI_UU_MO_RONG.md](BUOC_08_TOI_UU_MO_RONG.md) | Tối ưu hóa và mở rộng tính năng | 120 phút |

**⏱️ Tổng thời gian**: ~8 giờ (có thể chia thành nhiều session)

## 📁 Cấu trúc dự án

```
duan/
├── huongdan/           # Tài liệu hướng dẫn
│   ├── huongdanMd/     # File .md chi tiết
│   └── huongdanbanghinhanh/  # Hình ảnh minh họa
└── FooterThucHanh/     # Thực hành code
    └── FooterThucHanh/ # Dự án OrchardCore
        ├── FooterThucHanh.Web/     # Web project
        └── src/
            └── ThemeFooterDong/    # Custom theme
```

## Yêu cầu hệ thống

### 🔧 Công nghệ
- **.NET 8.0 SDK** (bắt buộc)
- **Visual Studio Code** hoặc Visual Studio
- **SQL Server** / **SQLite** / **PostgreSQL** / **MySQL**

### 📦 Packages chính
- `OrchardCore.ProjectTemplates::2.2.1-*`
- `Bootstrap 5.1.3`
- `Font Awesome 6.0.0`

### 🌐 Browsers hỗ trợ
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Cách sử dụng hướng dẫn

### 🚀 Bắt đầu nhanh
```bash
# 1. Clone hoặc download hướng dẫn
# 2. Đọc BUOC_01 để setup môi trường
# 3. Thực hiện từng bước theo thứ tự
# 4. Test kết quả sau mỗi bước
```

### 📖 Đọc hướng dẫn
- Mỗi file là 1 bước độc lập
- Có thể thực hiện từng phần riêng biệt
- Kiểm tra "Kết quả mong đợi" sau mỗi bước
- Tham khảo "Troubleshooting" khi gặp lỗi

### 🎯 Mục tiêu từng bước
1. **Bước 1-2**: Setup dự án và cấu trúc cơ bản
2. **Bước 3-4**: Tạo Content Types và Templates
3. **Bước 5-6**: Tạo dữ liệu và gán Widgets
4. **Bước 7-8**: Test và tối ưu hóa

## Kết quả cuối cùng

### 🎨 Giao diện Footer
```
┌─────────────────────────────────────────────────────────────┐
│                        FOOTER ZONE                          │
├─────────────────┬─────────────────┬─────────────────────────┤
│   LIÊN HỆ       │   GIỚI THIỆU    │     KẾT NỐI             │
│                 │                 │                         │
│ 🏢 Công ty ABC  │ 📝 Về chúng tôi │ 📱 Facebook             │
│ 📍 123 Đường XYZ│                 │ 🐦 Twitter              │
│ ☎️ 028.1234.5678│ Chúng tôi là... │ 📷 Instagram            │
│ ✉️ info@abc.com │                 │ 💼 LinkedIn             │
└─────────────────┴─────────────────┴─────────────────────────┘
│              © 2024 Company Name. All rights reserved.      │
└─────────────────────────────────────────────────────────────┘
```

### 🔧 Tính năng Admin Panel
- ✅ Chỉnh sửa thông tin liên hệ
- ✅ Thêm/sửa/xóa mạng xã hội
- ✅ Cập nhật nội dung giới thiệu
- ✅ Thay đổi thứ tự hiển thị
- ✅ Ẩn/hiện từng phần
- ✅ Preview trước khi publish

## Troubleshooting

### ❌ Lỗi thường gặp

**1. Footer không hiển thị**
```
Nguyên nhân: Theme chưa được set default
Giải pháp: Design → Themes → Set as Default
```

**2. Widget không xuất hiện trong danh sách**
```
Nguyên nhân: Content Type chưa có Stereotype = Widget
Giải pháp: Edit Content Type → Set Stereotype = Widget
```

**3. Template không hiển thị đúng**
```
Nguyên nhân: File template sai tên hoặc syntax lỗi
Giải pháp: Kiểm tra naming convention Widget-[ContentType].liquid
```

**4. CSS không load**
```
Nguyên nhân: Đường dẫn CSS sai hoặc cache
Giải pháp: Clear cache → Configuration → Performance
```

## Mở rộng tính năng

### 🚀 Tính năng nâng cao có thể thêm
- **Newsletter subscription** trong Footer
- **Quick links** menu
- **Multi-language** support
- **Google Maps** integration
- **Live chat** widget
- **Weather** widget
- **Stock ticker** widget

### 🔌 Tích hợp bên ngoài
- **Google Analytics** tracking
- **Facebook Pixel** integration
- **Email marketing** platforms
- **CRM** systems
- **Social media** APIs

## Tài liệu tham khảo

### 📚 OrchardCore
- [Official Documentation](https://docs.orchardcore.net/)
- [GitHub Repository](https://github.com/OrchardCMS/OrchardCore)
- [Community Forum](https://github.com/OrchardCMS/OrchardCore/discussions)

### 🎨 Frontend
- [Bootstrap 5 Docs](https://getbootstrap.com/docs/5.1/)
- [Font Awesome Icons](https://fontawesome.com/icons)
- [Liquid Template Language](https://shopify.github.io/liquid/)

### 🔍 SEO & Performance
- [Google PageSpeed Insights](https://pagespeed.web.dev/)
- [Schema.org](https://schema.org/)
- [Web.dev](https://web.dev/)

## Đóng góp

### 🤝 Cách đóng góp
1. Fork repository này
2. Tạo branch mới cho feature
3. Commit changes
4. Tạo Pull Request
5. Mô tả chi tiết thay đổi

### 📝 Báo lỗi
- Tạo Issue trên GitHub
- Mô tả chi tiết lỗi
- Kèm theo screenshot nếu có
- Ghi rõ môi trường (OS, .NET version, Browser)

## License

Dự án này được phát hành dưới **MIT License**. Xem file [LICENSE](LICENSE) để biết thêm chi tiết.

## Tác giả

**Phát triển bởi**: [Tên tác giả]  
**Email**: [email@domain.com]  
**Website**: [https://website.com]

---

### 🎉 Chúc bạn thành công với OrchardCore CMS!

> **Lưu ý**: Hướng dẫn này được viết dựa trên OrchardCore 2.2.1. Một số tính năng có thể thay đổi trong các phiên bản mới hơn.