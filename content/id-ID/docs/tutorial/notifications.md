# Pemberitahuan (Windows, Linux, macOS)

Ketiga sistem operasi tersebut menyediakan sarana bagi aplikasi untuk mengirim pemberitahuan ke pengguna. Elektron memudahkan pengembang untuk mengirim notifikasi dengan [HTML5 Notification API](https://notifications.spec.whatwg.org/), menggunakan API pemberitahuan asli sistem operasi yang sedang berjalan untuk menampilkannya.

**Catatan:** Karena ini adalah API HTML5, ini hanya tersedia dalam proses renderer. Jika Anda ingin menampilkan Notifikasi dalam proses utama, periksa modul [Notification](../api/notification.md).

```javascript
biarkan myNotification = baru pemberitahuan ('Title', {
  body: 'Lorem Ipsum Dolor Sit Amet'
}) myNotification.onclick = () = > {console.log ('notifikasi mengklik')}
```

Sementara kode dan pengalaman pengguna di seluruh sistem operasi serupa, ada perbedaan halus.

## Windows

* Pada Windows 10, notifikasi "just work".
* Pada Windows 8.1 dan Windows 8, jalan pintas ke aplikasi Anda, dengan [User ID Model Aplikasi](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378459(v=vs.85).aspx), harus diinstal ke layar Start. Namun perlu dicatat bahwa itu tidak perlu disematkan ke layar Start.
* Pada Windows 7, notifikasi bekerja melalui penerapan khusus yang secara visual menyerupai yang asli pada sistem yang lebih baru.

Selanjutnya, pada Windows 8, panjang maksimum untuk badan notifikasi adalah 250 karakter, dengan tim Windows merekomendasikan agar pemberitahuan harus disimpan hingga 200 karakter. Yang mengatakan, pembatasan itu telah dihapus di Windows 10, dengan tim Windows meminta pengembang untuk masuk akal. Mencoba mengirim sejumlah besar teks ke API (ribuan karakter) dapat menyebabkan ketidakstabilan.

### Pemberitahuan Lanjutan

Versi Windows selanjutnya memungkinkan pemberitahuan lanjutan, dengan template khusus, gambar, dan elemen fleksibel lainnya. Untuk mengirim pemberitahuan tersebut (dari proses utama atau proses renderer), menggunakan userland modul [elektron-windows-pemberitahuan](https://github.com/felixrieseberg/electron-windows-notifications), yang menggunakan asli Node addons untuk mengirim `ToastNotification` dan `TileNotification` objek.

While notifications including buttons work with `electron-windows-notifications`, handling replies requires the use of [`electron-windows-interactive-notifications`](https://github.com/felixrieseberg/electron-windows-interactive-notifications), which helps with registering the required COM components and calling your Electron app with the entered user data.

### Jam Tenang / Mode Presentasi

Untuk mendeteksi apakah Anda diizinkan mengirim pemberitahuan atau tidak, gunakan modul [pemberitahuan modul elektronika](https://github.com/felixrieseberg/electron-notification-state).

Hal ini memungkinkan Anda untuk menentukan sebelumnya apakah Windows diam-diam akan membuang notifikasi atau tidak.

## macOS

Notifikasi adalah lurus ke depan pada macOS, tetapi Anda harus menyadari [Apple Human Interface panduan mengenai pemberitahuan](https://developer.apple.com/library/mac/documentation/UserExperience/Conceptual/OSXHIGuidelines/NotificationCenter.html).

Perhatikan bahwa notifikasi dibatasi hingga 256 byte dan akan terpotong jika melebihi batas tersebut.

### Pemberitahuan Lanjutan

Versi macOS nanti memungkinkan pemberitahuan dengan bidang masukan, yang memungkinkan pengguna membalas dengan cepat ke pemberitahuan. Untuk mengirim notifikasi dengan field masukan, gunakan modul userland [node-mac-notifier ](https://github.com/CharlieHess/node-mac-notifier).

### Jangan ganggu / Sesi Negara

Untuk mendeteksi apakah Anda diizinkan mengirim pemberitahuan atau tidak, gunakan modul [pemberitahuan modul elektronika](https://github.com/felixrieseberg/electron-notification-state).

Ini akan memungkinkan Anda mendeteksi sebelumnya apakah pemberitahuan akan ditampilkan atau tidak.

## Linux

Notifikasi dikirim menggunakan `libnotify` yang dapat menampilkan pemberitahuan di lingkungan desktop mana pun yang mengikuti [Spesifikasi Pemberitahuan Desktop](https://developer.gnome.org/notification-spec/), termasuk Cinnamon, Enlightenment, Unity, GNOME, KDE.