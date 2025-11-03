# 🔍 CƠ CHẾ HOẠT ĐỘNG CỦA DỮ LIỆU - FOOTER 3 CỘT

## **📋 CƠ CHẾ HOẠT ĐỘNG CỦA 4 FILES:**

### **1. 🏗️ LAYOUT.LIQUID - FILE CHÍNH:**
```html
<!-- Layout.liquid - File chính định nghĩa cấu trúc -->
<footer class="footer-zone py-5 mt-5">
    <div class="container">
        <div class="row">
            <!-- Cột 1: Gọi FooterLeft zone -->
            <div class="col-md-4 mb-4">
                <div class="footer-card bg-primary">
                    {% render_section "FooterLeft", required: false %}  ← GỌI ZONE
                </div>
            </div>
            
            <!-- Cột 2: Gọi FooterCenter zone -->
            <div class="col-md-4 mb-4">
                <div class="footer-card bg-success">
                    {% render_section "FooterCenter", required: false %}  ← GỌI ZONE
                </div>
            </div>
            
            <!-- Cột 3: Gọi FooterRight zone -->
            <div class="col-md-4 mb-4">
                <div class="footer-card bg-info">
                    {% render_section "FooterRight", required: false %}  ← GỌI ZONE
                </div>
            </div>
        </div>
    </div>
</footer>
```

### **2. 🔄 QUY TRÌNH LOAD TEMPLATES:**

```
1. Browser request → Layout.liquid
2. Layout.liquid gặp {% render_section "FooterLeft" %}
3. OrchardCore tìm widgets trong FooterLeft zone
4. Tìm thấy FooterSocial widget → Load Widget-FooterSocial.liquid
5. Widget-FooterSocial.liquid render content → Trả về Layout.liquid
6. Layout.liquid tiếp tục {% render_section "FooterCenter" %}
7. Tìm thấy FooterAbout widget → Load Widget-FooterAbout.liquid
8. Widget-FooterAbout.liquid render content → Trả về Layout.liquid
9. Layout.liquid tiếp tục {% render_section "FooterRight" %}
10. Tìm thấy FooterContact widget → Load Widget-FooterContact.liquid
11. Widget-FooterContact.liquid render content → Trả về Layout.liquid
12. Layout.liquid hoàn thành → Gửi HTML về browser
```

### **3. 🎯 MAPPING ZONES ↔ TEMPLATES:**

| **Zone** | **Widget** | **Template File** | **Vị trí** |
|----------|------------|-------------------|-------------|
| `FooterLeft` | FooterSocial | `Widget-FooterSocial.liquid` | Cột 1 (Blue) |
| `FooterCenter` | FooterAbout | `Widget-FooterAbout.liquid` | Cột 2 (Green) |
| `FooterRight` | FooterContact | `Widget-FooterContact.liquid` | Cột 3 (Cyan) |

### **4. 📊 LUỒNG DỮ LIỆU:**

```
Admin Panel → Content Items → Widgets → Zones → Templates → Layout → Browser

1. Admin tạo content trong Admin Panel
2. Content được lưu thành Content Items
3. Content Items được gán vào Widgets
4. Widgets được đặt vào Zones (FooterLeft/Center/Right)
5. Layout.liquid gọi {% render_section "ZoneName" %}
6. OrchardCore tìm template tương ứng (Widget-*.liquid)
7. Template render data từ Content Items
8. Kết quả trả về Layout.liquid
9. Layout.liquid gửi HTML hoàn chỉnh về browser
```

## **5. 🔧 CHI TIẾT TECHNICAL:**

### **A. CÁCH ORCHARDCORE NHẬN DIỆN TEMPLATE:**
```
Widget Type: FooterSocial → Template: Widget-FooterSocial.liquid
Widget Type: FooterAbout → Template: Widget-FooterAbout.liquid
Widget Type: FooterContact → Template: Widget-FooterContact.liquid
```

### **B. CÁCH TEMPLATE TRUY CẬP DỮ LIỆU:**
```liquid
<!-- Widget-FooterSocial.liquid -->
{{ Model.ContentItem.Title.Text }}                    ← Title của widget
{{ Model.ContentItem.SocialUrl.Url }}                 ← URL mạng xã hội
{{ Model.ContentItem.SocialIcon.Text }}               ← Icon class

<!-- Widget-FooterAbout.liquid -->
{{ Model.ContentItem.AboutTitle.Text }}               ← Tiêu đề
{{ Model.ContentItem.AboutContent.Text }}             ← Nội dung

<!-- Widget-FooterContact.liquid -->
{{ Model.ContentItem.ContactTitle.Text }}             ← Tiêu đề liên hệ
{{ Model.ContentItem.CompanyName.Text }}              ← Tên công ty
{{ Model.ContentItem.Address.Text }}                  ← Địa chỉ
{{ Model.ContentItem.Phone.Text }}                    ← Số điện thoại
{{ Model.ContentItem.Email.Text }}                    ← Email
```

### **C. CÁCH ZONES ĐƯỢC QUẢN LÝ:**
```
1. Zones được khai báo trong Settings
2. Admin Panel → Layers → Widgets được gán vào zones
3. Layout.liquid gọi {% render_section "ZoneName" %}
4. OrchardCore render tất cả widgets trong zone đó
```

## **6. 🎯 WORKFLOW HOÀN CHỈNH:**

### **BƯỚC 1: ADMIN TẠO CONTENT**
```
Admin Panel → Content → Create New → FooterSocial
- Title: "Theo Dõi Chúng Tôi"
- SocialUrl: "https://facebook.com/company"
- SocialIcon: "fab fa-facebook"
```

### **BƯỚC 2: GÁN VÀO ZONE**
```
Admin Panel → Layers → Add Widget
- Widget Type: FooterSocial
- Zone: FooterLeft
- Position: 1
```

### **BƯỚC 3: RENDER PROCESS**
```
1. User truy cập website
2. Layout.liquid được load
3. Gặp {% render_section "FooterLeft" %}
4. OrchardCore tìm widgets trong FooterLeft zone
5. Tìm thấy FooterSocial widget
6. Load Widget-FooterSocial.liquid template
7. Template truy cập data từ Content Item
8. Render HTML với data
9. Trả kết quả về Layout.liquid
10. Layout.liquid tiếp tục render các zones khác
11. Gửi HTML hoàn chỉnh về browser
```

## **7. 🔍 DEBUG & TROUBLESHOOTING:**

### **A. KIỂM TRA ZONES:**
```
Admin Panel → Configuration → Settings → Zones
Đảm bảo có: FooterLeft, FooterCenter, FooterRight
```

### **B. KIỂM TRA WIDGETS:**
```
Admin Panel → Layers
Xem widgets nào được gán vào zone nào
```

### **C. KIỂM TRA TEMPLATES:**
```
Views/
├── Layout.liquid                    ← File chính
├── Widget-FooterSocial.liquid       ← Template FooterLeft
├── Widget-FooterAbout.liquid        ← Template FooterCenter
└── Widget-FooterContact.liquid      ← Template FooterRight
```

### **D. KIỂM TRA DATA:**
```
Admin Panel → Content → Content Items
Xem data có được lưu đúng không
```

## **8. ✅ TÓM TẮT:**

**ĐÚNG! Dự án sử dụng cả 4 files:**
- **1 file chính**: `Layout.liquid` (định nghĩa cấu trúc)
- **3 files template**: `Widget-*.liquid` (render nội dung từng zone)

**Layout.liquid KHÔNG trực tiếp load 3 files kia, mà:**
- Layout.liquid gọi `{% render_section "ZoneName" %}`
- OrchardCore engine tự động tìm và load template tương ứng
- Template render data và trả kết quả về Layout.liquid

**🎯 Đây là kiến trúc MVC pattern của OrchardCore!**

## **9. 🚀 KIẾN TRÚC TỔNG QUAN:**

```
┌─────────────────────────────────────────────────────────────┐
│                        BROWSER                              │
│                     (Hiển thị HTML)                         │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   LAYOUT.LIQUID                             │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │ FooterLeft  │ │FooterCenter │ │ FooterRight │           │
│  │   Zone      │ │    Zone     │ │    Zone     │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
└─────────┬───────────────┬───────────────┬───────────────────┘
          │               │               │
          ▼               ▼               ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│Widget-Footer│ │Widget-Footer│ │Widget-Footer│
│Social.liquid│ │About.liquid │ │Contact.liquid│
└─────────┬───┘ └─────────┬───┘ └─────────┬───┘
          │               │               │
          ▼               ▼               ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│FooterSocial │ │ FooterAbout │ │FooterContact│
│Content Item │ │Content Item │ │Content Item │
└─────────────┘ └─────────────┘ └─────────────┘
```

**🎉 FOOTER 3 CỘT HOẠT ĐỘNG HOÀN HẢO VỚI KIẾN TRÚC NÀY!**