# `features/admin` sebagai salinan verbatim stealth-forge

Seluruh UI Platform Admin di `features/admin/**` dipertahankan byte-identical dengan sumbernya di stealth-forge, termasuk token warna yang di-hardcode dan komentar aslinya. Tujuannya paritas visual dan kemudahan sinkron ulang: setiap file yang diubah lokal akan menjadi konflik saat upstream berubah, dan setiap token yang "dirapikan" akan membuat dua console berbeda tanpa ada yang bisa memutuskan mana yang benar. Konsekuensinya, adaptasi selalu dilakukan di sisi paas — halaman `app/admin/**` boleh mengganti jalur import, memberi `className` atau prop, atau menyusun ulang komposisi, tetapi tidak pernah mengedit file Forge. Perbedaan yang tidak bisa diselesaikan dari call site harus diperlakukan sebagai keputusan produk baru, bukan sebagai pembersihan kode.

## Amandemen 2026-11-28

Salinan lokal sekarang dinormalisasi Prettier (`printWidth: 100`) supaya seluruh repo lolos `npm run format:check`. Paritas byte dengan stealth-forge tidak lagi menjadi syarat; yang dipertahankan adalah paritas perilaku, markup, dan token visual. Saat menyinkronkan ulang dari upstream: salin file Forge, lalu jalankan `npx prettier --write features/admin`. Adaptasi tetap hanya di `app/admin/**`.
