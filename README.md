# app-srmc

Aplikasi web satu file (`index.html`), tanpa build step.

## Menjalankan lokal
Buka `index.html` di browser, atau:

    python3 -m http.server 8080

lalu buka http://localhost:8080

## Deploy
- **GitHub Pages**: Settings → Pages → Deploy from branch → `main` / root.
- **Hosting sendiri (Docker)**:

      docker build -t app-srmc .
      docker run -d -p 80:80 app-srmc

- Atau salin `index.html` ke folder web server mana pun (Nginx, Apache, Netlify, dll).

## Catatan penting
- Data disimpan di **localStorage browser** (mode "lokal") saat dijalankan di luar Claude. Data tidak dibagikan antar perangkat/pengguna, dan hilang jika cache browser dihapus. Rutin ekspor cadangan.
- Untuk data bersama banyak pengguna di hosting sendiri, perlu backend/database (misalnya Supabase atau Firebase) menggantikan lapisan `window.claude.use("db")`.
- Pustaka jsPDF dan SheetJS dimuat dari cdnjs; font dari Google Fonts (perlu internet).
