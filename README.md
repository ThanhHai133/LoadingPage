# EDCLoading
# ✨ EDC Loading Overlay

Hiệu ứng loading chữ "EDC..." chỉ cần thêm vào và gọi thêm sử dụng.  
**Tương thích với mọi nền tảng: Blazor, ASP.NET MVC, ASP.NET Core API, Web Forms, React, Vue, Laravel, HTML...**

---

## 🚀 Cách sử dụng

### 1. ✅ **Copy file `edc-loader.html` vào thư mục public của bạn**

| Loại dự án                 | Thư mục để đặt `edc-loader.html`             |
|----------------------------|----------------------------------------------|
| **Blazor Server**          | `wwwroot/css/edc-loader.html`                |
| **ASP.NET Core MVC / API** | `wwwroot/css/edc-loader.html`                |
| **ASP.NET Web Forms**      | `~/Content/edc-loader.html` hoặc `~/css/`    |
| **ASP.NET MVC (classic)**  | `~/Content/edc-loader.html` hoặc `~/css/`    |
| **HTML / PHP**             | Chung thư mục với `index.html`               |
| **React / Vue**            | `public/edc-loader.html`                     |
| **Laravel**                | `public/css/edc-loader.html`                 |
| **Next.js**                | `public/edc-loader.html`                     |

---

### 2. ✅ **Thêm đoạn sau vào layout của trang chính**

**Chèn trước `</body>` trong layout hoặc trang gốc:**

```html
<!-- Container để load loader -->
<div id="edc-loader-container"></div>

<!-- Script để hiển thị và tự động ẩn loader -->
<script>
  fetch('/css/edc-loader.html') // ⚠️ Đổi path nếu bạn để ở chỗ khác
    .then(res => res.text())
    .then(html => {
      document.getElementById('edc-loader-container').innerHTML = html;

      // ✅ Set Time cho loading Tự động ẩn loader sau 3 giây
      setTimeout(() => {
        document.getElementById('edc-loading-overlay')?.classList.add('d-none');
      }, 3000);
    });

  // ✅ Dùng trong JS / Blazor để điều khiển thủ công
  window.EDCLoader = {
    show: () => document.getElementById('edc-loading-overlay')?.classList.remove('d-none'),
    hide: () => document.getElementById('edc-loading-overlay')?.classList.add('d-none')
  };
</script>
