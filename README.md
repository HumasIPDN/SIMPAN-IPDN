# SIMPAN IPDN — GitHub Pages Wrapper

Folder ini dipakai untuk membungkus aplikasi publik Google Apps Script
menggunakan domain GitHub Pages atau custom domain.

## File

- `index.html` — wrapper iframe publik
- `logo-simpan.png` — logo baru SIMPAN
- `404.html` — mengembalikan rute ke halaman utama
- `CNAME.example` — contoh custom domain

## Yang harus diganti pada index.html

Cari `APP_CONFIG`, lalu isi:

```javascript
PUBLIC_APP_URL: "https://script.google.com/macros/s/ID-PUBLIK/exec",
ADMIN_APP_URL: "https://script.google.com/macros/s/ID-ADMIN/exec?mode=admin",
```

Admin dibuka langsung di tab baru, bukan di dalam iframe.

## Aktifkan GitHub Pages

1. Buat repository GitHub.
2. Upload seluruh isi folder ini ke root repository.
3. Buka Settings → Pages.
4. Source: Deploy from a branch.
5. Branch: main.
6. Folder: /root.
7. Save.

## Custom domain

Untuk subdomain seperti `simpan.ipdn.ac.id`, tambahkan custom domain
di Settings → Pages, lalu minta pengelola DNS membuat CNAME menuju:

```text
USERNAME-GITHUB.github.io
```

## Penting

Google Apps Script publik harus memakai:

```javascript
.setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL)
```

Halaman admin tidak diizinkan masuk iframe dan tetap wajib akun
`humas@ipdn.ac.id`.
