# arkzz-asisten-update

Pusat update ARKZZ ASISTEN. Repository ini harus **Public**.

Isi repository:

- `latest.json` : informasi versi terbaru yang dibaca aplikasi
- `README.md` : berkas ini

APK tidak disimpan di dalam repository, tetapi diunggah ke **GitHub Releases**.

## Menerbitkan versi baru

1. Perbarui source aplikasi.
2. Naikkan `versionCode` dan ubah `versionName` di `app/build.gradle`.
3. Build APK dengan **signing key yang sama** seperti versi sebelumnya (simpan cadangan keystore).
4. Di GitHub: Releases > Draft a new release, buat tag (misalnya `v1.4.0`), lalu unggah APK.
5. Salin alamat unduhan APK dari halaman release (`https://github.com/PEMILIK/REPO/releases/download/TAG/NAMA.apk`).
6. Edit `latest.json`: samakan `versionCode` dan `versionName` dengan APK, isi `apkUrl`, `releaseNotes`, lalu Commit.
7. Selesai. Aplikasi akan menemukan update saat dibuka atau dalam 12 jam.

Contoh `latest.json` untuk versi 1.4.0:

```json
{
  "versionCode": 19,
  "versionName": "1.4.0",
  "apkUrl": "https://github.com/arkzztoolsofficial-king/arkzz-asisten-update/releases/download/v1.4.0/ARKZZ_ASISTEN_1.4.0.apk",
  "releaseNotes": [
    "Peningkatan sistem AI",
    "Perbaikan bug",
    "Penambahan fitur baru"
  ],
  "mandatory": false
}
```

## Aturan

- `versionCode` di `latest.json` harus sama dengan `versionCode` di APK. Bila beda, aplikasi menolak memasangnya.
- Hanya `versionCode` yang LEBIH TINGGI dari versi terpasang yang dianggap update.
- `apkUrl` harus `https://github.com/PEMILIK/...` (PEMILIK = `UPDATE_GITHUB_OWNER` di `ArkzzConfig.java`) dan berakhiran `.apk`.
- `mandatory: true` menampilkan dialog tanpa tombol NANTI. Pemasangan tetap dikonfirmasi pengguna lewat installer Android.
- Jangan terbitkan `latest.json` yang `versionCode`-nya lebih tinggi sebelum APK-nya selesai diunggah ke Release.
