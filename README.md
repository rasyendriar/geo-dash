# GeoDash Pro

Konverter KML ⇄ CSV berbasis browser (murni HTML/JS statis, tanpa backend).

## Menjalankan secara lokal

Cukup buka `index.html` di browser, atau jalankan server statis apa saja, misalnya:

```bash
python3 -m http.server 8000
```

lalu buka `http://localhost:8000`.

## Hosting di GitHub Pages

Repo ini sudah berupa situs statis (`index.html` di root), jadi tidak perlu proses build. Aktifkan sekali saja:

1. Buka **Settings → Pages** di repo GitHub ini.
2. Pada **Build and deployment → Source**, pilih **Deploy from a branch**.
3. Pilih branch `main` dan folder `/ (root)`, lalu **Save**.
4. Tunggu beberapa menit, situs akan tersedia di `https://<username>.github.io/<nama-repo>/`.

`converter.html` tetap ada sebagai redirect otomatis ke `index.html`, untuk menjaga tautan lama tetap berfungsi.

## Catatan performa

Pemrosesan file besar (KML/CSV dengan banyak baris) dijalankan secara bertahap (chunked) dengan progress bar, CSV di-stream langsung dari `File` (bukan dibaca penuh ke memori dulu), dan preview peta dibatasi jumlah fitur yang digambar untuk mencegah tab browser freeze pada dataset besar.
