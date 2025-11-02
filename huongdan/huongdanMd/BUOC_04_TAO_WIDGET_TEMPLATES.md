# BƯỚC 4: TẠO WIDGET TEMPLATES

## Mục tiêu
Tạo các template Liquid để hiển thị Widgets Footer với giao diện đẹp và responsive.

## Kiến thức cần biết
- **Widget Template**: Template hiển thị Widget
- **Shape Alternates**: Tùy chỉnh template theo Content Type
- **Liquid Syntax**: Cú pháp template của OrchardCore

## Cấu trúc Template cần tạo

### 1. Widget-FooterContact.liquid
### 2. Widget-FooterSocial.liquid  
### 3. Widget-FooterAbout.liquid

## Các bước thực hiện

### BƯỚC 4.1: Tạo FooterContact Widget Template

#### 1. Tạo file template
**Đường dẫn**: `src/ThemeFooterDong/Views/Widget-FooterContact.liquid`

```liquid
{% comment %}
Template hiển thị Widget Footer Contact
Sử dụng Bootstrap classes cho responsive design
{% endcomment %}

<div class="footer-contact-widget">
    <h5 class="footer-title">
        <i class="fas fa-building me-2"></i>
        Liên Hệ
    </h5>
    
    <div class="contact-info">
        {% if Model.ContentItem.FooterContact.CompanyName.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-building me-2"></i>
            <span>{{ Model.ContentItem.FooterContact.CompanyName.Text }}</span>
        </div>
        {% endif %}
        
        {% if Model.ContentItem.FooterContact.Address.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-map-marker-alt me-2"></i>
            <span>{{ Model.ContentItem.FooterContact.Address.Text }}</span>
        </div>
        {% endif %}
        
        {% if Model.ContentItem.FooterContact.Phone.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-phone me-2"></i>
            <a href="tel:{{ Model.ContentItem.FooterContact.Phone.Text }}" class="text-decoration-none">
                {{ Model.ContentItem.FooterContact.Phone.Text }}
            </a>
        </div>
        {% endif %}
        
        {% if Model.ContentItem.FooterContact.Email.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-envelope me-2"></i>
            <a href="mailto:{{ Model.ContentItem.FooterContact.Email.Text }}" class="text-decoration-none">
                {{ Model.ContentItem.FooterContact.Email.Text }}
            </a>
        </div>
        {% endif %}
    </div>
</div>
```

### BƯỚC 4.2: Tạo FooterSocial Widget Template

#### 1. Tạo file template
**Đường dẫn**: `src/ThemeFooterDong/Views/Widget-FooterSocial.liquid`

```liquid
{% comment %}
Template hiển thị Widget Footer Social
Hiển thị các liên kết mạng xã hội với icons
{% endcomment %}

<div class="footer-social-widget">
    <h5 class="footer-title">
        <i class="fas fa-share-alt me-2"></i>
        Kết Nối
    </h5>
    
    <div class="social-links">
        {% if Model.ContentItem.FooterSocial.SocialUrl.Text %}
        <a href="{{ Model.ContentItem.FooterSocial.SocialUrl.Text }}" 
           target="_blank" 
           class="social-link me-3 mb-2 d-inline-block"
           title="{{ Model.ContentItem.FooterSocial.SocialName.Text }}">
            {% if Model.ContentItem.FooterSocial.SocialIcon.Text %}
                <i class="{{ Model.ContentItem.FooterSocial.SocialIcon.Text }} fa-lg"></i>
            {% else %}
                <i class="fas fa-link fa-lg"></i>
            {% endif %}
            <span class="ms-2">{{ Model.ContentItem.FooterSocial.SocialName.Text }}</span>
        </a>
        {% endif %}
    </div>
</div>

<style>
.social-link {
    color: #adb5bd !important;
    transition: color 0.3s ease;
}

.social-link:hover {
    color: #ffffff !important;
    text-decoration: none;
}

.social-link i {
    width: 20px;
    text-align: center;
}
</style>
```

### BƯỚC 4.3: Tạo FooterAbout Widget Template

#### 1. Tạo file template
**Đường dẫn**: `src/ThemeFooterDong/Views/Widget-FooterAbout.liquid`

```liquid
{% comment %}
Template hiển thị Widget Footer About
Hiển thị thông tin giới thiệu công ty
{% endcomment %}

<div class="footer-about-widget">
    {% if Model.ContentItem.FooterAbout.AboutTitle.Text %}
    <h5 class="footer-title">
        <i class="fas fa-info-circle me-2"></i>
        {{ Model.ContentItem.FooterAbout.AboutTitle.Text }}
    </h5>
    {% endif %}
    
    {% if Model.ContentItem.FooterAbout.AboutDescription.Text %}
    <div class="about-content">
        {{ Model.ContentItem.FooterAbout.AboutDescription.Text }}
    </div>
    {% endif %}
</div>

<style>
.about-content p {
    color: #adb5bd;
    line-height: 1.6;
    margin-bottom: 1rem;
}

.about-content a {
    color: #ffffff;
    text-decoration: underline;
}

.about-content a:hover {
    color: #adb5bd;
}
</style>
```

### BƯỚC 4.4: Tạo CSS chung cho Footer Widgets

#### 1. Cập nhật file CSS
**Đường dẫn**: `src/ThemeFooterDong/wwwroot/css/site.css`

```css
/* Footer Widget Styles */
.footer-zone .widget-container {
    margin-bottom: 2rem;
}

.footer-title {
    color: #ffffff !important;
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 1rem;
    border-bottom: 2px solid #495057;
    padding-bottom: 0.5rem;
}

.footer-title i {
    color: #007bff;
}

.contact-item {
    display: flex;
    align-items: flex-start;
    color: #adb5bd;
}

.contact-item i {
    color: #007bff;
    width: 20px;
    margin-top: 2px;
}

.contact-item a {
    color: #adb5bd;
    transition: color 0.3s ease;
}

.contact-item a:hover {
    color: #ffffff;
    text-decoration: none;
}

/* Responsive Design */
@media (max-width: 768px) {
    .footer-zone .row > div {
        margin-bottom: 2rem;
    }
    
    .footer-title {
        font-size: 1rem;
    }
    
    .contact-item {
        font-size: 0.9rem;
    }
}
```

### BƯỚC 4.5: Cấu hình Placement (Tùy chọn)

#### 1. Tạo file Placement.json
**Đường dẫn**: `src/ThemeFooterDong/Placement.json`

```json
{
  "Widget-FooterContact": {
    "place": "Content:1"
  },
  "Widget-FooterSocial": {
    "place": "Content:1"
  },
  "Widget-FooterAbout": {
    "place": "Content:1"
  }
}
```

## Kiểm tra kết quả

### 1. Kiểm tra files đã tạo
```
src/ThemeFooterDong/
├── Views/
│   ├── Widget-FooterContact.liquid ✅
│   ├── Widget-FooterSocial.liquid ✅
│   └── Widget-FooterAbout.liquid ✅
├── wwwroot/css/
│   └── site.css (đã cập nhật) ✅
└── Placement.json ✅
```

### 2. Test template
- Tạo thử 1 Widget để xem template hiển thị
- Kiểm tra responsive trên mobile

## Kết quả mong đợi
- Templates hiển thị đúng định dạng
- Icons Font Awesome hoạt động
- Responsive design trên mobile
- CSS styling đẹp mắt

## Bước tiếp theo
→ **BƯỚC 5**: Tạo Content Items qua Admin Panel

## Ghi chú quan trọng
- **Widget-[ContentType].liquid** là naming convention chuẩn
- Sử dụng `Model.ContentItem.[FieldName].Text/Html/Url` để truy xuất dữ liệu
- Bootstrap classes đảm bảo responsive design