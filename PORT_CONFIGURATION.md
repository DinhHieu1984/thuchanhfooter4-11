# 🔧 HƯỚNG DẪN CẤU HÌNH CỔNG CHO FOOTER 3 CỘT

## ⚠️ VẤN ĐỀ: Cổng khác nhau có thể gây mất dữ liệu

### 🔍 NGUYÊN NHÂN:
- OrchardCore có thể tạo database riêng cho mỗi cổng/URL
- Site configuration khác nhau giữa các máy
- Base URL khác nhau → OrchardCore nghĩ là 2 site khác nhau

---

## 🛠️ GIẢI PHÁP 1: CHẠY CÙNG CỔNG

### Cách 1: Chỉ định cổng cố định
```bash
cd FooterThucHanh
dotnet run --urls=http://localhost:5000
```

### Cách 2: Sử dụng launchSettings.json
```json
{
  "profiles": {
    "FooterThucHanh.Web": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "http://localhost:5000",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

---

## 🛠️ GIẢI PHÁP 2: CẤU HÌNH SITE SETTINGS

### Kiểm tra Site Settings trong Admin:
1. Vào **Configuration → Settings → General**
2. Kiểm tra **Base URL** 
3. Đảm bảo **Site Name** giống nhau

### Cấu hình trong appsettings.json:
```json
{
  "OrchardCore": {
    "OrchardCore_Tenants": {
      "Default": {
        "RequestUrlHost": "localhost:5000",
        "RequestUrlPrefix": ""
      }
    }
  }
}
```

---

## 🛠️ GIẢI PHÁP 3: COPY DATABASE TRỰC TIẾP

### Nếu vẫn không hoạt động:
1. **Backup database hiện tại:**
   ```bash
   cp App_Data/Sites/Default/OrchardCore.db OrchardCore.backup.db
   ```

2. **Xóa database cũ:**
   ```bash
   rm App_Data/Sites/Default/OrchardCore.db
   ```

3. **Copy database từ GitHub:**
   ```bash
   git checkout HEAD -- FooterThucHanh/FooterThucHanh.Web/App_Data/Sites/Default/OrchardCore.db
   ```

4. **Restart ứng dụng:**
   ```bash
   dotnet run --urls=http://localhost:5000
   ```

---

## 🎯 KHUYẾN NGHỊ

### ✅ CÁCH TỐT NHẤT:
1. **Luôn chạy trên cổng 5000:** `dotnet run --urls=http://localhost:5000`
2. **Tạo launchSettings.json** để cố định cổng
3. **Kiểm tra Site Settings** trong Admin Panel

### ⚠️ LƯU Ý:
- Mỗi cổng khác nhau có thể tạo database riêng
- Đảm bảo Base URL nhất quán giữa các máy
- Backup database trước khi thay đổi cấu hình

---

## 📞 KIỂM TRA

Sau khi cấu hình:
1. Truy cập: `http://localhost:5000`
2. Footer phải hiển thị 3 cột màu sắc
3. Admin Panel: `http://localhost:5000/Admin`

**🎉 Database sẽ được sử dụng đúng và Footer hiển thị hoàn hảo!**