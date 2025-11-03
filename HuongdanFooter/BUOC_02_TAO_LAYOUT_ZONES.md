# BƯỚC 2: TẠO LAYOUT VÀ 3 ZONES FOOTER RIÊNG BIỆT

## 🎯 Mục tiêu
Tạo Layout.liquid với **3 ZONES FOOTER RIÊNG BIỆT** để tránh trùng lặp dữ liệu.

## ⚠️ VẤN ĐỀ QUAN TRỌNG NHẤT
**NGUYÊN NHÂN GỐC RỄ GÂY TRÙNG LẶP DỮ LIỆU:**
- ❌ **1 Footer zone duy nhất** → Cả 3 cột hiển thị cùng nội dung
- ✅ **3 Footer zones riêng biệt** → Mỗi cột hiển thị nội dung khác nhau

## 📚 Kiến thức cần biết
- **Layout**: Template chính định nghĩa cấu trúc trang
- **Zone**: Vùng hiển thị có thể chứa Widgets
- **Liquid**: Template engine của OrchardCore
- **{% render_section %}**: Syntax CHÍNH THỨC để render zones

---

## 🔧 CÁC BƯỚC THỰC HIỆN

### **BƯỚC 2.1: CẤU HÌNH 3 ZONES RIÊNG BIỆT**

#### 📍 2.1.1: Truy cập Settings (HƯỚNG DẪN CHI TIẾT)
1. **Đăng nhập Admin Panel**: 
   - Mở trình duyệt web
   - Truy cập: `http://localhost:41481/Admin`
   - Đăng nhập với tài khoản admin đã tạo

2. **Vào mục Zones (ĐÚNG)**: 
   - Click vào **"Design"** (menu bên trái) để mở rộng menu
   - Click vào **"Settings"** 
   - Click vào **"Zones"**
   - **Đường dẫn trực tiếp**: `http://localhost:41481/Admin/Settings/Zones`

⚠️ **LƯU Ý**: Không phải "Configuration" → "Settings" như hướng dẫn cũ!

#### ⚙️ 2.1.2: Khai báo Zones (CHI TIẾT)
1. **Tìm phần "Available zones for Layers"**:
   - Sẽ thấy ô text input có sẵn nội dung: `Content`
   
2. **Thêm zones mới**:
   - Đặt con trỏ chuột vào cuối từ `Content`
   - Thêm dấu phẩy và khoảng trắng: `, `
   - Gõ thêm: `FooterLeft, FooterCenter, FooterRight`
   
3. **Kết quả cuối cùng**:
```
Content, FooterLeft, FooterCenter, FooterRight
```

**⚠️ LƯU Ý QUAN TRỌNG:**
- **KHÔNG dùng**: `Content, Footer` (gây trùng lặp)
- **PHẢI dùng**: `Content, FooterLeft, FooterCenter, FooterRight`
- **Phân cách bằng dấu phẩy và khoảng trắng**
- **Chính xác như hình ảnh đã chụp**

#### 💾 2.1.3: Lưu Settings (CHI TIẾT)
1. **Click nút "Save"** (màu xanh ở cuối trang)
2. **Hệ thống sẽ hiển thị thông báo thành công**
3. **Trang sẽ reload và hiển thị zones đã được cập nhật**

#### 🔍 2.1.4: Kiểm tra Zones đã tạo
1. Vào **Design** → **Widgets**
2. Khi tạo widget mới, sẽ thấy dropdown **"Zone"** có 4 lựa chọn:
   - Content
   - FooterLeft
   - FooterCenter
   - FooterRight

---

### **BƯỚC 2.2: TẠO LAYOUT.LIQUID ĐÚNG**

#### 📁 2.2.1: Vị trí file CHÍNH XÁC
**File**: `src/ThemeFooterDong/Views/Layout.liquid`

⚠️ **LƯU Ý QUAN TRỌNG:**
- **Layout.liquid**: Nằm trực tiếp trong Views/ (không cần Shared/)
- **Widget templates**: Cũng nằm trong Views/

#### 📝 2.2.2: Nội dung Layout.liquid CHÍNH XÁC
```liquid
<!DOCTYPE html>
<html lang="{{ Culture.Name }}">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{% if Model.Title %}{{ Model.Title }} - {% endif %}{{ Site.SiteName }}</title>
    
    <!-- Bootstrap 5 CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    {% render_section "HeadMeta", required: false %}
    {% render_section "HeadLinks", required: false %}
    {% render_section "HeadScript", required: false %}
</head>
<body>
    <!-- Header -->
    <header class="bg-light py-3 mb-4">
        <div class="container">
            <div class="row align-items-center">
                <div class="col">
                    <h1 class="h3 mb-0">
                        <a href="{{ '~/' | href }}" class="text-decoration-none text-dark">
                            {{ Site.SiteName }}
                        </a>
                    </h1>
                </div>
                <div class="col-auto">
                    {% render_section "Header", required: false %}
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container">
        {% render_section "Messages", required: false %}
        
        <div class="row">
            <div class="col-md-9">
                {% render_section "Content", required: false %}
            </div>
            <div class="col-md-3">
                {% render_section "Sidebar", required: false %}
            </div>
        </div>
    </main>

    <!-- ⭐ FOOTER 3 CỘT - QUAN TRỌNG NHẤT ⭐ -->
    <footer class="py-5 mt-5" style="background: #f8f9fa;">
        <div class="container">
            <div class="row">
                <!-- 🔵 Cột 1: FooterLeft Zone - Màu xanh dương -->
                <div class="col-md-4 mb-4">
                    <div class="bg-primary text-white p-4 rounded shadow h-100">
                        {% render_section "FooterLeft", required: false %}
                    </div>
                </div>
                
                <!-- 🟢 Cột 2: FooterCenter Zone - Màu xanh lá -->
                <div class="col-md-4 mb-4">
                    <div class="bg-success text-white p-4 rounded shadow h-100">
                        {% render_section "FooterCenter", required: false %}
                    </div>
                </div>
                
                <!-- 🔷 Cột 3: FooterRight Zone - Màu xanh cyan -->
                <div class="col-md-4 mb-4">
                    <div class="bg-info text-white p-4 rounded shadow h-100">
                        {% render_section "FooterRight", required: false %}
                    </div>
                </div>
            </div>
        </div>
    </footer>

    <!-- Bootstrap 5 JS -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    
    {% render_section "FootScript", required: false %}
</body>
</html>
```

### **BƯỚC 2.3: TẠO CSS CUSTOM (TÙY CHỌN)**

#### 📁 2.3.1: Tạo file CSS
**File**: `src/ThemeFooterDong/wwwroot/css/site.css`
```css
/* Footer Custom Styles */
.footer-card {
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.footer-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.15) !important;
}

.footer-card h1, .footer-card h2, .footer-card h3, 
.footer-card h4, .footer-card h5 {
    color: white !important;
    margin-bottom: 1rem;
}

.footer-card p, .footer-card div {
    color: rgba(255, 255, 255, 0.9) !important;
}

.footer-card a {
    color: white !important;
    text-decoration: none;
}

.footer-card a:hover {
    color: rgba(255, 255, 255, 0.8) !important;
}
```

#### 📝 2.3.2: Include CSS vào Layout
**Thêm vào `<head>` của Layout.liquid:**
```liquid
<!-- Custom CSS -->
<link href="~/ThemeFooterDong/css/site.css" rel="stylesheet">
```

---

## 🔍 SO SÁNH SYNTAX SAI VÀ ĐÚNG

### ❌ **SYNTAX SAI (GÂY TRÙNG LẶP):**
```liquid
<!-- SAI: Cả 3 cột đều render cùng 1 zone -->
<div class="col-md-4">{{ "Footer" | shape_render }}</div>
<div class="col-md-4">{{ "Footer" | shape_render }}</div>  
<div class="col-md-4">{{ "Footer" | shape_render }}</div>
```

### ✅ **SYNTAX ĐÚNG (KHÔNG TRÙNG LẶP):**
```liquid
<!-- ĐÚNG: Mỗi cột render zone riêng biệt -->
<div class="col-md-4">{% render_section "FooterLeft", required: false %}</div>
<div class="col-md-4">{% render_section "FooterCenter", required: false %}</div>
<div class="col-md-4">{% render_section "FooterRight", required: false %}</div>
```

---

## ✅ KIỂM TRA KẾT QUẢ

### 🔍 2.3.1: Xác nhận Zones đã tạo
1. **Vào Admin Panel → Design → Widgets**
2. **Click "Add Widget"**
3. **Kiểm tra dropdown "Zone":**
   - ✅ **FooterLeft** (xuất hiện)
   - ✅ **FooterCenter** (xuất hiện)
   - ✅ **FooterRight** (xuất hiện)
   - ❌ **Footer** (KHÔNG còn xuất hiện)

### 🎨 2.3.2: Kiểm tra Layout hiển thị
1. **Truy cập website**: `http://localhost:5000`
2. **Kiểm tra Footer:**
   - ✅ **3 cột màu sắc khác nhau**: Blue, Green, Cyan
   - ✅ **Mỗi cột độc lập** (không trùng lặp nội dung)
   - ✅ **Responsive design** (mobile-friendly)

---

## 🎯 KẾT QUẢ MONG ĐỢI

### ✅ Đã hoàn thành:
- **3 Zones riêng biệt**: FooterLeft, FooterCenter, FooterRight
- **Layout.liquid đúng syntax**: `{% render_section "ZoneName" %}`
- **Footer 3 cột màu sắc**: Blue, Green, Cyan
- **Không trùng lặp dữ liệu**: Mỗi zone độc lập
- **Bootstrap 5 + FontAwesome**: Responsive và icons

---

## 🚀 BƯỚC TIẾP THEO

→ **BƯỚC 3**: Tạo Content Types cho Footer

---

## ⚠️ LƯU Ý QUAN TRỌNG

### 🔴 **Điểm quan trọng nhất:**
- **3 Zones riêng biệt**: FooterLeft, FooterCenter, FooterRight
- **Syntax chính thức**: `{% render_section "ZoneName" %}`
- **Không dùng Footer zone**: Gây trùng lặp dữ liệu

### 🔧 **Nếu không hiển thị 3 cột:**
1. **Kiểm tra Zones Settings**: Phải có FooterLeft, FooterCenter, FooterRight
2. **Kiểm tra Layout.liquid**: Phải dùng `{% render_section %}`
3. **Restart application**: `dotnet run` lại
4. **Clear cache**: Refresh trình duyệt