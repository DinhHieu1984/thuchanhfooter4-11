# BƯỚC 1: TẠO DỰ ÁN ORCHARDCORE CMS

## Mục tiêu
Tạo dự án OrchardCore CMS chuẩn để xây dựng Footer động có thể quản trị qua Admin Panel.

## Yêu cầu hệ thống
- .NET 8.0 SDK
- Visual Studio Code hoặc Visual Studio
- OrchardCore.ProjectTemplates

## Các bước thực hiện

### 1. Cài đặt OrchardCore Project Templates
```bash
dotnet new install OrchardCore.ProjectTemplates::2.2.1-*
```

### 2. Tạo dự án OrchardCore CMS
```bash
# Tạo thư mục dự án chính
mkdir FooterThucHanh
cd FooterThucHanh

# Tạo solution
dotnet new sln -n FooterThucHanh

# Tạo dự án Web CMS
dotnet new occms -n FooterThucHanh.Web

# Thêm Web project vào solution
dotnet sln add FooterThucHanh.Web/FooterThucHanh.Web.csproj

# Tạo thư mục src cho themes
mkdir src

# Tạo theme trong thư mục src
cd src
dotnet new octheme -n ThemeFooterDong

# Thêm theme project vào solution
cd ..
dotnet sln add src/ThemeFooterDong/ThemeFooterDong.csproj
```

### 3. Cấu trúc dự án được tạo (theo chuẩn OrchardCore)
```
FooterThucHanh/
├── FooterThucHanh.sln                    # Solution file
├── FooterThucHanh.Web/                   # Web CMS Project
│   ├── Program.cs                        # Entry point
│   ├── appsettings.json                  # Configuration
│   ├── Properties/launchSettings.json    # Launch settings
│   ├── FooterThucHanh.Web.csproj        # Web project file
│   └── wwwroot/                         # Static files
└── src/                                 # Source folder
    └── ThemeFooterDong/                 # Theme Project
        ├── ThemeFooterDong.csproj       # Theme project file
        ├── Manifest.cs                  # Theme manifest
        └── Views/
            └── Layout.liquid            # Layout template
```

### 4. Thêm reference Theme vào Web project
```bash
# Thêm reference theme vào web project
cd FooterThucHanh.Web
dotnet add reference ../src/ThemeFooterDong/ThemeFooterDong.csproj
```

### 5. Chạy dự án lần đầu
```bash
# Từ thư mục FooterThucHanh.Web
dotnet run
```

### 6. Thiết lập ban đầu
1. Mở trình duyệt: `https://localhost:5001`
2. Chọn **Setup** để cấu hình
3. Chọn **SQLite** làm database
4. Tạo tài khoản Admin
5. Chọn recipe **Blog** hoặc **Blank Site**

### 7. Kích hoạt các modules cần thiết
Vào Admin Panel → Configuration → Features, kích hoạt:
- ✅ **Content Types** (quản lý Content Types)
- ✅ **Widgets** (tạo widgets)
- ✅ **Layers** (gán widgets vào zones)
- ✅ **Liquid** (template engine)
- ✅ **Templates** (quản lý templates)

## Kết quả mong đợi
- Dự án OrchardCore CMS chạy thành công
- Truy cập được Admin Panel
- Các modules cần thiết đã được kích hoạt

## Bước tiếp theo
→ **BƯỚC 2**: Tạo Layout với Zones để định nghĩa vùng Footer

## Ghi chú quan trọng
- OrchardCore sử dụng kiến trúc **modular** và **multi-tenant**
- Mọi thứ đều có thể quản trị qua Admin Panel
- Footer sẽ được tạo thành **Widget** và gán vào **Zone**