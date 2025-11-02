# BƯỚC 2: TẠO LAYOUT VÀ ZONES

## Mục tiêu
Tạo Layout.liquid với các Zones chuẩn OrchardCore, bao gồm Footer Zone để hiển thị Footer động.

## Kiến thức cần biết
- **Layout**: Template chính định nghĩa cấu trúc trang
- **Zone**: Vùng hiển thị có thể chứa Widgets
- **Liquid**: Template engine của OrchardCore

## Các bước thực hiện

### 1. Sử dụng Theme đã tạo
Theme **ThemeFooterDong** đã được tạo trong BƯỚC 1, nằm trong thư mục `src/ThemeFooterDong/`

### 2. Cấu trúc Theme hiện tại
```
src/ThemeFooterDong/
├── ThemeFooterDong.csproj
├── Manifest.cs
├── Views/
│   └── Layout.liquid
├── wwwroot/
│   ├── css/
│   └── js/
└── Placement.json (sẽ tạo)
```

### 3. Tạo Layout.liquid chuẩn
**File: Views/Layout.liquid**
```liquid
<!DOCTYPE html>
<html lang="{{ Culture.Name }}">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{% if Model.Title %}{{ Model.Title }} - {% endif %}{{ Site.SiteName }}</title>
    
    <!-- Meta tags zone -->
    {{ "HeadMeta" | shape_render }}
    
    <!-- CSS resources -->
    {{ "HeadLinks" | shape_render }}
    
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
</head>
<body>
    <!-- Header Zone -->
    <header class="header-zone">
        <div class="container">
            {{ "Header" | shape_render }}
        </div>
    </header>

    <!-- Navigation Zone -->
    <nav class="navigation-zone">
        <div class="container">
            {{ "Navigation" | shape_render }}
        </div>
    </nav>

    <!-- Main Content -->
    <main class="main-content">
        <div class="container">
            <!-- Content Zone -->
            <div class="content-zone">
                {{ Model.Content | shape_render }}
            </div>
            
            <!-- Sidebar Zone -->
            <aside class="sidebar-zone">
                {{ "Sidebar" | shape_render }}
            </aside>
        </div>
    </main>

    <!-- Footer Zone - QUAN TRỌNG -->
    <footer class="footer-zone bg-dark text-light py-4">
        <div class="container">
            {{ "Footer" | shape_render }}
        </div>
    </footer>

    <!-- Scripts Zone -->
    {{ "FootScript" | shape_render }}
    
    <!-- Bootstrap JS -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

### 4. Cấu hình Manifest.cs
**File: Manifest.cs**
```csharp
using OrchardCore.DisplayManagement.Manifest;

[assembly: Theme(
    Name = "FooterDong Theme",
    Author = "Your Name",
    Website = "https://yourwebsite.com",
    Version = "1.0.0",
    Description = "Theme với Footer động cho OrchardCore",
    Tags = new[] { "Bootstrap", "Footer", "Dynamic" }
)]
```

### 5. Tạo CSS tùy chỉnh
**File: src/ThemeFooterDong/wwwroot/css/site.css**
```css
/* Footer Styles */
.footer-zone {
    margin-top: auto;
    background-color: #343a40 !important;
}

.footer-zone .widget-container {
    margin-bottom: 1rem;
}

.footer-zone h5 {
    color: #ffffff;
    margin-bottom: 1rem;
}

.footer-zone p, .footer-zone a {
    color: #adb5bd;
}

.footer-zone a:hover {
    color: #ffffff;
    text-decoration: none;
}

/* Responsive */
@media (max-width: 768px) {
    .footer-zone .row > div {
        margin-bottom: 2rem;
    }
}
```

### 6. Kích hoạt Theme
1. Vào Admin Panel → Design → Themes
2. Tìm **ThemeFooterDong**
3. Click **Set as Default**

### 7. Kiểm tra Zones
Vào Admin Panel → Design → Widgets để xem các zones có sẵn:
- ✅ Header
- ✅ Navigation  
- ✅ Content
- ✅ Sidebar
- ✅ **Footer** (quan trọng nhất)

## Kết quả mong đợi
- Layout hiển thị đúng cấu trúc
- Footer Zone xuất hiện trong danh sách Widgets
- Theme được áp dụng thành công

## Bước tiếp theo
→ **BƯỚC 3**: Tạo Content Types cho Footer (FooterContact, FooterSocial)

## Ghi chú quan trọng
- **Footer Zone** là nơi sẽ chứa các Widgets động
- Liquid template cho phép render Zones linh hoạt
- Bootstrap được tích hợp sẵn cho responsive design