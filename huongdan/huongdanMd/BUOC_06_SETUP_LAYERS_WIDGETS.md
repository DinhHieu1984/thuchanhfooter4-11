# BƯỚC 6: SETUP LAYERS VÀ GÁN WIDGETS VÀO FOOTER ZONE

## Mục tiêu
Sử dụng Layers để gán các Widgets vào Footer Zone, tạo Footer động hiển thị trên tất cả trang.

## Kiến thức cần biết
- **Layer**: Quy tắc hiển thị Widget (hiển thị ở đâu, khi nào)
- **Zone**: Vùng hiển thị trong Layout (Footer, Header, Sidebar...)
- **Widget**: Thành phần hiển thị được gán vào Zone thông qua Layer

## Layers cần sử dụng

### 1. Default Layer (Hiển thị trên tất cả trang)
### 2. Homepage Layer (Chỉ hiển thị trên trang chủ - nếu cần)

## Các bước thực hiện

### BƯỚC 6.1: Kiểm tra Layers có sẵn

#### 1. Truy cập Layers Management
- Vào **Design → Widgets**
- Xem danh sách **Layers** ở phía trên

#### 2. Layers mặc định của OrchardCore
```
✅ Default (Rule: "true" - Hiển thị trên tất cả trang)
✅ Homepage (Rule: "isHomepage()" - Chỉ hiển thị trang chủ)
✅ Authenticated (Rule: "isAuthenticated()" - User đã đăng nhập)
✅ Anonymous (Rule: "isAnonymous()" - User chưa đăng nhập)
```

### BƯỚC 6.2: Gán Footer Contact Widget

#### 1. Chọn Layer
- Trong **Design → Widgets**
- Chọn **Default Layer** (để hiển thị trên tất cả trang)

#### 2. Thêm Widget vào Footer Zone
- Tìm **Footer Zone** trong danh sách zones
- Click **Add Widget** trong Footer Zone
- Chọn **Footer Contact** từ danh sách

#### 3. Cấu hình Widget
```
Widget Configuration:
├── Title: "Thông Tin Liên Hệ" (hoặc để trống)
├── Content Item: Chọn "Thông Tin Liên Hệ Công Ty"
├── Position: 1 (hiển thị đầu tiên)
└── Zone: Footer (đã được chọn sẵn)
```

#### 4. Save Widget
- Click **Save** để lưu cấu hình

### BƯỚC 6.3: Gán Footer Social Widgets

#### 1. Thêm Facebook Widget
```
Zone: Footer
Widget Type: Footer Social
Content Item: "Facebook Page"
Position: 2
Title: "" (để trống)
```

#### 2. Thêm Twitter Widget
```
Zone: Footer
Widget Type: Footer Social
Content Item: "Twitter Profile"
Position: 3
Title: "" (để trống)
```

#### 3. Thêm Instagram Widget
```
Zone: Footer
Widget Type: Footer Social
Content Item: "Instagram Profile"
Position: 4
Title: "" (để trống)
```

#### 4. Thêm LinkedIn Widget
```
Zone: Footer
Widget Type: Footer Social
Content Item: "LinkedIn Company"
Position: 5
Title: "" (để trống)
```

### BƯỚC 6.4: Gán Footer About Widget

#### 1. Thêm About Widget
```
Zone: Footer
Widget Type: Footer About
Content Item: "Giới Thiệu Công Ty"
Position: 6
Title: "" (để trống)
```

### BƯỚC 6.5: Tối ưu Layout Footer

#### 1. Cập nhật Layout.liquid để responsive
**File**: `src/ThemeFooterDong/Views/Layout.liquid`

```liquid
<!-- Footer Zone - Cập nhật với Bootstrap Grid -->
<footer class="footer-zone bg-dark text-light py-4">
    <div class="container">
        <div class="row">
            <!-- Contact Info Column -->
            <div class="col-md-4 mb-3">
                {{ "Footer" | shape_render | where: "ContentType", "FooterContact" }}
            </div>
            
            <!-- About Column -->
            <div class="col-md-4 mb-3">
                {{ "Footer" | shape_render | where: "ContentType", "FooterAbout" }}
            </div>
            
            <!-- Social Links Column -->
            <div class="col-md-4 mb-3">
                <h5 class="footer-title">
                    <i class="fas fa-share-alt me-2"></i>
                    Kết Nối Với Chúng Tôi
                </h5>
                <div class="social-links-container">
                    {{ "Footer" | shape_render | where: "ContentType", "FooterSocial" }}
                </div>
            </div>
        </div>
        
        <!-- Copyright Row -->
        <div class="row mt-4 pt-3 border-top">
            <div class="col-12 text-center">
                <p class="mb-0 text-muted">
                    © {{ "now" | date: "yyyy" }} {{ Site.SiteName }}. All rights reserved.
                </p>
            </div>
        </div>
    </div>
</footer>
```

#### 2. Cập nhật CSS cho layout mới
**File**: `src/ThemeFooterDong/wwwroot/css/site.css`

```css
/* Footer Layout Styles */
.footer-zone {
    background: linear-gradient(135deg, #343a40 0%, #495057 100%);
    border-top: 3px solid #007bff;
}

.social-links-container {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}

.social-links-container .footer-social-widget {
    margin-bottom: 0;
}

.social-links-container .social-link {
    display: inline-flex;
    align-items: center;
    padding: 0.5rem 1rem;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 25px;
    transition: all 0.3s ease;
}

.social-links-container .social-link:hover {
    background: rgba(0, 123, 255, 0.8);
    transform: translateY(-2px);
}

/* Responsive adjustments */
@media (max-width: 768px) {
    .social-links-container {
        justify-content: center;
    }
    
    .footer-zone .col-md-4 {
        text-align: center;
    }
}
```

## Kiểm tra kết quả

### 1. Xem danh sách Widgets
Trong **Design → Widgets → Default Layer → Footer Zone**:
```
✅ Footer Contact (Position: 1)
✅ Footer Social - Facebook (Position: 2)
✅ Footer Social - Twitter (Position: 3)
✅ Footer Social - Instagram (Position: 4)
✅ Footer Social - LinkedIn (Position: 5)
✅ Footer About (Position: 6)
```

### 2. Test trên Frontend
- Mở trang web
- Kiểm tra Footer hiển thị đầy đủ thông tin
- Test responsive trên mobile
- Kiểm tra links social media hoạt động

### 3. Test trên nhiều trang
- Trang chủ: Footer hiển thị ✅
- Trang About: Footer hiển thị ✅
- Trang Blog: Footer hiển thị ✅
- Trang Contact: Footer hiển thị ✅

## Quản lý Widgets

### 1. Thay đổi thứ tự hiển thị
```
1. Vào Design → Widgets
2. Chọn Default Layer
3. Trong Footer Zone, kéo thả để sắp xếp
4. Hoặc edit Widget và thay đổi Position
```

### 2. Tạm thời ẩn Widget
```
1. Edit Widget cần ẩn
2. Uncheck "Published"
3. Save → Widget sẽ không hiển thị
```

### 3. Thêm Widget mới
```
1. Tạo Content Item mới (Bước 5)
2. Vào Design → Widgets
3. Add Widget vào Footer Zone
4. Chọn Content Item vừa tạo
```

## Kết quả mong đợi
- Footer hiển thị đầy đủ trên tất cả trang
- Layout responsive trên mobile
- Thông tin có thể chỉnh sửa qua Admin Panel
- Social links hoạt động chính xác

## Bước tiếp theo
→ **BƯỚC 7**: Test và tối ưu hóa Footer động

## ⚠️ CÁC LỖI THƯỜNG GẶP VÀ CÁCH KHẮC PHỤC

### 🚫 LỖI 1: Footer không hiển thị
**Nguyên nhân:**
- Chưa tạo Content Items cho Widgets
- Chưa gán Widgets vào Footer Zone
- Layout.liquid chưa có `render_section "Footer"`

**Giải pháp:**
```liquid
<!-- Đảm bảo Layout.liquid có dòng này -->
{% render_section "Footer", required: false %}
```

### 🚫 LỖI 2: Chỉ hiển thị tiêu đề, không có nội dung
**Nguyên nhân:** Widget templates truy cập sai cách dữ liệu

**❌ Cách SAI:**
```liquid
{{ Model.ContentItem.Content.FooterContact.CompanyName.Text }}
```

**✅ Cách ĐÚNG:**
```liquid
{{ Model.ContentItem.FooterContact.CompanyName.Text }}
```

**📋 TEMPLATE MẪU ĐÚNG CHO TỪNG WIDGET:**

#### Widget-FooterContact.liquid
```liquid
<div class="footer-contact-widget">
    <h5 class="footer-title text-white mb-3">
        <i class="fas fa-building me-2"></i>
        Liên Hệ
    </h5>
    
    <div class="contact-info">
        {% if Model.ContentItem.FooterContact.CompanyName.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-building me-2 text-primary"></i>
            <span class="text-light">{{ Model.ContentItem.FooterContact.CompanyName.Text }}</span>
        </div>
        {% endif %}
        
        {% if Model.ContentItem.FooterContact.Address.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-map-marker-alt me-2 text-primary"></i>
            <span class="text-light">{{ Model.ContentItem.FooterContact.Address.Text }}</span>
        </div>
        {% endif %}
        
        {% if Model.ContentItem.FooterContact.Phone.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-phone me-2 text-primary"></i>
            <a href="tel:{{ Model.ContentItem.FooterContact.Phone.Text }}" class="text-light text-decoration-none">
                {{ Model.ContentItem.FooterContact.Phone.Text }}
            </a>
        </div>
        {% endif %}
        
        {% if Model.ContentItem.FooterContact.Email.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-envelope me-2 text-primary"></i>
            <a href="mailto:{{ Model.ContentItem.FooterContact.Email.Text }}" class="text-light text-decoration-none">
                {{ Model.ContentItem.FooterContact.Email.Text }}
            </a>
        </div>
        {% endif %}
    </div>
</div>
```

#### Widget-FooterSocial.liquid
```liquid
<div class="footer-social-widget d-inline-block me-3">
    <div class="social-links">
        {% if Model.ContentItem.FooterSocial.SocialUrl.Text %}
        <a href="{{ Model.ContentItem.FooterSocial.SocialUrl.Text }}" 
           target="_blank" 
           rel="noopener noreferrer"
           class="social-link text-decoration-none"
           title="{{ Model.ContentItem.FooterSocial.SocialName.Text }}"
           style="color: #adb5bd; transition: color 0.3s ease;">
            {% if Model.ContentItem.FooterSocial.SocialIcon.Text %}
                <i class="{{ Model.ContentItem.FooterSocial.SocialIcon.Text }} fa-2x" style="width: 40px; text-align: center;"></i>
            {% else %}
                <i class="fas fa-link fa-2x" style="width: 40px; text-align: center;"></i>
            {% endif %}
        </a>
        {% endif %}
    </div>
</div>
```

#### Widget-FooterAbout.liquid
```liquid
<div class="footer-about-widget">
    {% if Model.ContentItem.FooterAbout.AboutTitle.Text %}
    <h5 class="footer-title text-white mb-3">
        <i class="fas fa-info-circle me-2"></i>
        {{ Model.ContentItem.FooterAbout.AboutTitle.Text }}
    </h5>
    {% endif %}
    
    {% if Model.ContentItem.FooterAbout.AboutContent.Text %}
    <div class="about-content">
        <p class="text-light mb-0" style="line-height: 1.6;">
            {{ Model.ContentItem.FooterAbout.AboutContent.Text }}
        </p>
    </div>
    {% endif %}
</div>
```

### 🚫 LỖI 3: Layout hiển thị 1 cột thay vì 3 cột
**Nguyên nhân:** Zone templates không hoạt động với Liquid themes

**Giải pháp:** Sử dụng CSS Grid trong Layout.liquid
```liquid
<footer class="footer-zone bg-dark text-light py-5">
    <div class="container">
        <div class="footer-grid">
            {% render_section "Footer", required: false %}
        </div>
    </div>
</footer>

<style>
.footer-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 2rem;
    align-items: start;
}

/* Widget đầu tiên - Liên Hệ */
.footer-grid > *:nth-child(1) {
    grid-column: 1;
}

/* Widgets 2-5 - Kết Nối */
.footer-grid > *:nth-child(2),
.footer-grid > *:nth-child(3),
.footer-grid > *:nth-child(4),
.footer-grid > *:nth-child(5) {
    grid-column: 2;
    display: inline-block;
    margin-right: 15px;
}

/* Widget cuối - Thông Tin */
.footer-grid > *:nth-child(6) {
    grid-column: 3;
}

/* Responsive */
@media (max-width: 768px) {
    .footer-grid {
        grid-template-columns: 1fr;
        gap: 1.5rem;
    }
    
    .footer-grid > * {
        grid-column: 1 !important;
    }
}
</style>
```

### 🚫 LỖI 4: Widget templates không hoạt động
**Nguyên nhân:** Tên file template không đúng convention

**✅ Tên file ĐÚNG:**
```
Widget-FooterContact.liquid
Widget-FooterSocial.liquid  
Widget-FooterAbout.liquid
```

**❌ Tên file SAI:**
```
FooterContact.liquid
footer-contact.liquid
Widget_FooterContact.liquid
```

## 🔧 CHECKLIST KIỂM TRA TRƯỚC KHI BẮT ĐẦU

### ✅ Trước khi gán Widgets:
- [ ] Đã tạo đầy đủ Content Types (Bước 4)
- [ ] Đã tạo đầy đủ Content Items (Bước 5)  
- [ ] Đã tạo đầy đủ Widget Templates (Bước 5)
- [ ] Layout.liquid có `render_section "Footer"`

### ✅ Sau khi gán Widgets:
- [ ] Footer hiển thị trên frontend
- [ ] Có đầy đủ nội dung (không chỉ tiêu đề)
- [ ] Layout 3 cột hoạt động đúng
- [ ] Responsive trên mobile
- [ ] Social links hoạt động

## 🎯 THỨ TỰ POSITION KHUYẾN NGHỊ

```
Position 1: Footer Contact (Cột 1)
Position 3: Facebook Social (Cột 2)  
Position 4: Twitter Social (Cột 2)
Position 5: Instagram Social (Cột 2)
Position 6: LinkedIn Social (Cột 2)
Position 9: Footer About (Cột 3)
```

**Lưu ý:** Sử dụng position 3,4,5,6 cho social để tạo khoảng cách, position 9 cho About để đảm bảo hiển thị cuối cùng.

## 🔍 TROUBLESHOOTING NÂNG CAO

### 🛠️ Debug Widget Templates
Nếu widget không hiển thị đúng, thêm debug code:

```liquid
<!-- Debug: Kiểm tra dữ liệu có tồn tại không -->
<div style="background: red; color: white; padding: 10px;">
    DEBUG: {{ Model.ContentItem | json }}
</div>

<!-- Debug: Kiểm tra từng field -->
<p>CompanyName: "{{ Model.ContentItem.FooterContact.CompanyName.Text }}"</p>
<p>Address: "{{ Model.ContentItem.FooterContact.Address.Text }}"</p>
```

### 🛠️ Kiểm tra Widget đã được gán đúng chưa
1. Vào **Design → Widgets**
2. Chọn **Default Layer**
3. Kiểm tra **Footer Zone** có đầy đủ widgets
4. Kiểm tra **Position** và **Published status**

### 🛠️ Xóa cache nếu thay đổi không hiển thị
```bash
# Trong terminal
cd /path/to/project
dotnet build
# Hoặc restart application
```

### 🛠️ Kiểm tra Content Items có dữ liệu
1. Vào **Content → Content Items**
2. Tìm Content Items đã tạo
3. Edit và kiểm tra các field có dữ liệu
4. Đảm bảo **Published** status

## 🎯 BEST PRACTICES

### ✅ Quy tắc đặt tên
```
Content Type: FooterContact (PascalCase)
Template File: Widget-FooterContact.liquid (kebab-case với prefix)
CSS Class: footer-contact-widget (kebab-case)
```

### ✅ Cấu trúc thư mục khuyến nghị
```
Views/
├── Layout.liquid
├── Widget-FooterContact.liquid
├── Widget-FooterSocial.liquid
├── Widget-FooterAbout.liquid
└── Zone-Footer.liquid (không hoạt động với Liquid)
```

### ✅ Performance Tips
- Sử dụng `cache-id` cho widgets ít thay đổi
- Tối ưu CSS bằng cách tách ra file riêng
- Sử dụng CDN cho Font Awesome icons

## 🚨 GIẢI PHÁP CHUẨN: FOOTER 3 CỘT KHỐI MÀU KHÁC NHAU

### ❌ VẤN ĐỀ THƯỜNG GẶP: "NHẢY LOẠN" FOOTER

**Nguyên nhân gốc rễ:**
1. **Over-engineering**: Tạo quá nhiều FooterQuad zones không cần thiết
2. **Duplicate content**: Hardcode social icons + render zones → hiển thị 2 lần
3. **CSS phức tạp**: Grid layout phức tạp thay vì Bootstrap đơn giản
4. **Không tham khảo code gốc OrchardCore**

### ✅ GIẢI PHÁP CHUẨN THEO ORCHARDCORE

#### 1. Học từ OrchardCore Source Code

**TheBlogTheme - Siêu đơn giản:**
```liquid
<footer class="border-top">
    {% render_section "Footer", required: false %}
</footer>
```

**TheAgencyTheme - Social icons chuẩn:**
```liquid
{% if member.TeamMember.Twitter.Text.size > 0 %}
<a class="btn btn-dark btn-social mx-2" href="https://www.twitter.com/{{ member.TeamMember.Twitter.Text }}">
    <i class="fab fa-x-twitter"></i>
</a>
{% endif %}
```

#### 2. Layout Footer 3 Cột Khối Màu - CÁCH ĐÚNG

**File**: `src/ThemeFooterDong/Views/Layout.liquid`

```liquid
<!-- Footer đơn giản - 3 cột màu xanh khác nhau -->
<footer class="footer-zone py-5">
    <div class="container">
        <div class="row">
            <!-- Cột 1: Xanh dương -->
            <div class="col-md-4 mb-4">
                <div class="footer-card bg-primary text-white p-4 rounded shadow">
                    <h4><i class="fas fa-share-alt"></i> Kết Nối Với Chúng Tôi</h4>
                    <div class="social-icons d-flex gap-3 mt-3">
                        <a href="https://facebook.com" class="btn btn-light btn-sm" target="_blank" title="Facebook">
                            <i class="fab fa-facebook-f"></i>
                        </a>
                        <a href="https://twitter.com" class="btn btn-light btn-sm" target="_blank" title="Twitter">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="https://linkedin.com" class="btn btn-light btn-sm" target="_blank" title="LinkedIn">
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                        <a href="https://instagram.com" class="btn btn-light btn-sm" target="_blank" title="Instagram">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="https://youtube.com" class="btn btn-light btn-sm" target="_blank" title="YouTube">
                            <i class="fab fa-youtube"></i>
                        </a>
                    </div>
                </div>
            </div>
            
            <!-- Cột 2: Xanh lá -->
            <div class="col-md-4 mb-4">
                <div class="footer-card bg-success text-white p-4 rounded shadow">
                    <h4><i class="fas fa-clock"></i> Giờ Làm Việc</h4>
                    <div class="mt-3">
                        <p><i class="fas fa-calendar-alt me-2"></i> Thứ 2 - Thứ 6: 8:00 - 17:00</p>
                        <p><i class="fas fa-calendar-alt me-2"></i> Thứ 7: 8:00 - 12:00</p>
                        <p><i class="fas fa-times-circle me-2"></i> Chủ nhật: Nghỉ</p>
                    </div>
                </div>
            </div>
            
            <!-- Cột 3: Xanh teal -->
            <div class="col-md-4 mb-4">
                <div class="footer-card bg-info text-white p-4 rounded shadow">
                    <h4><i class="fas fa-info-circle"></i> Thông Tin Liên Hệ</h4>
                    <div class="mt-3">
                        <p><i class="fas fa-map-marker-alt me-2"></i> 123 Đường ABC, Quận XYZ</p>
                        <p><i class="fas fa-phone me-2"></i> (84) 123-456-789</p>
                        <p><i class="fas fa-envelope me-2"></i> info@example.com</p>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Copyright -->
        <hr class="my-4">
        <div class="row">
            <div class="col-12 text-center">
                <p class="mb-0 text-muted">
                    © 2024 FooterThucHanh. Tất cả quyền được bảo lưu.
                    <span class="ms-3">
                        <i class="fas fa-code me-1"></i>
                        Được phát triển với OrchardCore
                    </span>
                </p>
            </div>
        </div>
    </div>
</footer>
```

#### 3. CSS Đơn Giản - Chiều Cao Bằng Nhau

```css
/* Đảm bảo 3 cột có chiều cao bằng nhau */
.footer-zone .row {
    display: flex;
    align-items: stretch;
}

.footer-card {
    height: 100%;
    display: flex;
    flex-direction: column;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.footer-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.15) !important;
}

.social-icons .btn {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
}

.social-icons .btn:hover {
    transform: scale(1.1);
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}
```

### 🎯 TẠI SAO CÁCH NÀY TỐT HƠN?

#### ✅ Ưu điểm của giải pháp chuẩn:
1. **Bootstrap Grid**: `col-md-4` tự động responsive
2. **Bootstrap Colors**: `bg-primary`, `bg-success`, `bg-info` - chuẩn design system
3. **Flexbox đơn giản**: `d-flex gap-3` cho social icons xếp ngang
4. **Equal Height**: `align-items: stretch` + `height: 100%`
5. **FontAwesome chuẩn**: Theo convention OrchardCore
6. **Không duplicate**: Chỉ 1 nguồn dữ liệu duy nhất
7. **Dễ maintain**: Code đơn giản, dễ hiểu

#### ❌ Vấn đề của cách cũ:
1. **FooterQuad zones**: Phức tạp không cần thiết
2. **CSS Grid phức tạp**: 50+ dòng CSS responsive
3. **Duplicate content**: Hardcode + zones
4. **Over-engineering**: Không học từ code gốc

### 🔧 MIGRATION GUIDE: TỪ WIDGETS SANG HARDCODE

#### Bước 1: Backup dữ liệu từ Content Items
```bash
# Export content items trước khi thay đổi
# Vào Admin → Content → Content Items
# Copy thông tin: Company name, address, phone, email, social links
```

#### Bước 2: Thay thế Layout.liquid
```liquid
<!-- XÓA phần cũ -->
<div class="footer-quad-container">
    {% render_section "FooterQuadFirst", required: false %}
    <!-- ... các zones phức tạp khác -->
</div>

<!-- THAY BẰNG phần mới -->
<div class="row">
    <div class="col-md-4 mb-4">
        <div class="footer-card bg-primary text-white p-4 rounded shadow">
            <!-- Nội dung cố định -->
        </div>
    </div>
</div>
```

#### Bước 3: Cập nhật thông tin thực tế
```liquid
<!-- Thay thế thông tin mẫu bằng thông tin thực -->
<p><i class="fas fa-map-marker-alt me-2"></i> {{ ĐỊACHỈ_THỰC_TẾ }}</p>
<p><i class="fas fa-phone me-2"></i> {{ SỐ_ĐIỆN_THOẠI_THỰC_TẾ }}</p>
<p><i class="fas fa-envelope me-2"></i> {{ EMAIL_THỰC_TẾ }}</p>

<!-- Social links thực tế -->
<a href="{{ FACEBOOK_URL_THỰC_TẾ }}" class="btn btn-light btn-sm">
    <i class="fab fa-facebook-f"></i>
</a>
```

### 🎨 CUSTOMIZATION OPTIONS

#### Thay đổi màu sắc:
```liquid
<!-- Thay vì bg-primary, bg-success, bg-info -->
<div class="footer-card bg-danger">    <!-- Đỏ -->
<div class="footer-card bg-warning">   <!-- Vàng -->
<div class="footer-card bg-secondary"> <!-- Xám -->
```

#### Thêm gradient:
```css
.footer-card.bg-primary {
    background: linear-gradient(135deg, #007bff 0%, #0056b3 100%) !important;
}
```

#### Responsive breakpoints:
```liquid
<!-- Thay col-md-4 thành: -->
<div class="col-lg-4 col-md-6 col-sm-12"> <!-- 3 cột desktop, 2 cột tablet, 1 cột mobile -->
```

### 📊 SO SÁNH HIỆU SUẤT

| Tiêu chí | Cách cũ (Widgets) | Cách mới (Hardcode) |
|----------|-------------------|---------------------|
| **Số dòng CSS** | 150+ dòng | 30 dòng |
| **Số zones** | 4 zones phức tạp | 0 zones |
| **Database queries** | 6 queries | 0 queries |
| **Load time** | Chậm hơn | Nhanh hơn |
| **Maintenance** | Phức tạp | Đơn giản |
| **Responsive** | CSS phức tạp | Bootstrap tự động |

### 🎯 KHI NÀO DÙNG WIDGETS VS HARDCODE?

#### ✅ Dùng Widgets khi:
- Nội dung thay đổi thường xuyên
- Nhiều người quản lý nội dung
- Cần đa ngôn ngữ
- Nội dung phức tạp (rich text, images)

#### ✅ Dùng Hardcode khi:
- Nội dung ít thay đổi (footer, header)
- Chỉ developer quản lý
- Cần performance cao
- Layout đơn giản, cố định

### 🔍 DEBUGGING TIPS

#### Kiểm tra layout responsive:
```bash
# Test trên các kích thước màn hình
# Desktop: >= 992px → 3 cột
# Tablet: 768-991px → 2 cột  
# Mobile: < 768px → 1 cột
```

#### Kiểm tra hover effects:
```css
/* Debug hover bằng cách thêm border */
.footer-card:hover {
    border: 2px solid yellow !important;
}
```

## Ghi chú quan trọng
- **KISS Principle**: Keep It Simple, Stupid - Đơn giản là tốt nhất
- **Tham khảo code gốc**: Luôn học từ OrchardCore source code trước khi implement
- **Bootstrap First**: Sử dụng Bootstrap thay vì CSS custom phức tạp
- **Equal Height**: `align-items: stretch` + `height: 100%` cho cột bằng nhau
- **Performance**: Hardcode nhanh hơn widgets cho nội dung ít thay đổi
- **Responsive**: Bootstrap grid tự động responsive, không cần CSS phức tạp
- **Maintenance**: Code đơn giản dễ maintain hơn code phức tạp
- **Convention**: Học từ TheAgencyTheme và TheBlogTheme về cách làm social icons