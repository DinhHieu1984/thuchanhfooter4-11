# 🚨 TROUBLESHOOTING FOOTER WIDGETS - QUICK REFERENCE

## 🔥 CÁC LỖI THƯỜNG GẶP VÀ GIẢI PHÁP NHANH

### ❌ Footer không hiển thị
```liquid
<!-- Kiểm tra Layout.liquid có dòng này -->
{% render_section "Footer", required: false %}
```

### ❌ Chỉ có tiêu đề, không có nội dung
```liquid
<!-- SAI -->
{{ Model.ContentItem.Content.FooterContact.CompanyName.Text }}

<!-- ĐÚNG -->
{{ Model.ContentItem.FooterContact.CompanyName.Text }}
```

### ❌ Layout 1 cột thay vì 3 cột
```css
/* Thêm CSS Grid vào Layout.liquid */
.footer-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 2rem;
}

.footer-grid > *:nth-child(1) { grid-column: 1; }
.footer-grid > *:nth-child(2),
.footer-grid > *:nth-child(3),
.footer-grid > *:nth-child(4),
.footer-grid > *:nth-child(5) { 
    grid-column: 2; 
    display: inline-block; 
    margin-right: 15px; 
}
.footer-grid > *:nth-child(6) { grid-column: 3; }
```

### ❌ Widget template không hoạt động
```
✅ ĐÚNG: Widget-FooterContact.liquid
❌ SAI:  FooterContact.liquid
❌ SAI:  footer-contact.liquid
❌ SAI:  Widget_FooterContact.liquid
```

## 🔧 CHECKLIST NHANH

### Trước khi gán Widgets:
- [ ] Content Types đã tạo (FooterContact, FooterSocial, FooterAbout)
- [ ] Content Items đã tạo và có dữ liệu
- [ ] Widget templates đã tạo với tên đúng
- [ ] Layout.liquid có `render_section "Footer"`

### Sau khi gán Widgets:
- [ ] Footer hiển thị trên frontend
- [ ] Có đầy đủ nội dung (không chỉ tiêu đề)
- [ ] Layout 3 cột hoạt động
- [ ] Responsive trên mobile

## 🛠️ DEBUG NHANH

### Kiểm tra dữ liệu Widget:
```liquid
<!-- Thêm vào widget template để debug -->
<div style="background: red; color: white; padding: 10px;">
    DEBUG: {{ Model.ContentItem | json }}
</div>
```

### Kiểm tra Widget đã gán:
1. **Design → Widgets → Default Layer → Footer Zone**
2. Kiểm tra Position và Published status

### Clear cache:
```bash
dotnet build
# Hoặc restart application
```

## 🎯 POSITION KHUYẾN NGHỊ

```
Position 1: Footer Contact (Cột 1)
Position 3: Facebook Social (Cột 2)  
Position 4: Twitter Social (Cột 2)
Position 5: Instagram Social (Cột 2)
Position 6: LinkedIn Social (Cột 2)
Position 9: Footer About (Cột 3)
```

## 📋 TEMPLATE MẪU NHANH

### Widget-FooterContact.liquid
```liquid
<div class="footer-contact-widget">
    <h5 class="footer-title text-white mb-3">
        <i class="fas fa-building me-2"></i>Liên Hệ
    </h5>
    <div class="contact-info">
        {% if Model.ContentItem.FooterContact.CompanyName.Text %}
        <div class="contact-item mb-2">
            <i class="fas fa-building me-2 text-primary"></i>
            <span class="text-light">{{ Model.ContentItem.FooterContact.CompanyName.Text }}</span>
        </div>
        {% endif %}
        <!-- Thêm các field khác tương tự -->
    </div>
</div>
```

### Widget-FooterSocial.liquid
```liquid
<div class="footer-social-widget d-inline-block me-3">
    {% if Model.ContentItem.FooterSocial.SocialUrl.Text %}
    <a href="{{ Model.ContentItem.FooterSocial.SocialUrl.Text }}" 
       target="_blank" class="social-link text-decoration-none"
       style="color: #adb5bd;">
        <i class="{{ Model.ContentItem.FooterSocial.SocialIcon.Text }} fa-2x"></i>
    </a>
    {% endif %}
</div>
```

## ⚡ GIẢI PHÁP NHANH NHẤT

Nếu gặp vấn đề, làm theo thứ tự:

1. **Kiểm tra Content Items có dữ liệu**
2. **Kiểm tra Widget templates tên đúng**
3. **Kiểm tra Layout.liquid có render_section**
4. **Build lại project**
5. **Kiểm tra Widgets đã gán vào Footer Zone**
6. **Thêm CSS Grid nếu layout không đúng**

## 🎉 KẾT QUẢ MONG ĐỢI

- ✅ Footer hiển thị 3 cột đều nhau
- ✅ Cột 1: Thông tin liên hệ đầy đủ
- ✅ Cột 2: 4 social links inline
- ✅ Cột 3: Thông tin về công ty
- ✅ Responsive trên mobile (1 cột)
- ✅ Icons và styling đẹp mắt