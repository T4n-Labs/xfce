# T4n OS XFCE Dotfiles

Konfigurasi dan dotfiles XFCE untuk **T4n OS** (berbasis Void Linux): tema, ikon, font, wallpaper, panel, shortcut, dan konfigurasi aplikasi pendukung, lengkap dengan script instalasi otomatis.

[Source Code](https://github.com/diws1/xfce-customize)

## Isi

| Komponen | Detail |
|---|---|
| Tema GTK dan window manager | Ant-Nebula |
| Ikon | Tela |
| Font | JetBrainsMono dan RobotoMono (Nerd Font) |
| Wallpaper | `desert.jpg` (default), `triangle-void.png`, `void1.png`, `void2.png` |
| Panel | bar bawah transparan (Whisker Menu, pager, tasklist, power, notifikasi, volume, jam) dan dock launcher vertikal auto-hide di sisi kiri |
| Aplikasi | conky (autostart), cava (dengan shader dan tema), tilda, Thunar, xfce4-terminal |
| Shortcut | keyboard shortcut XFCE kustom, termasuk screenshot dan mic mute |
| Sistem | konfigurasi touchpad libinput (tap to click, natural scrolling) |

## Kebutuhan

- Void Linux dengan XFCE yang sudah terpasang
- `sudo` dan koneksi internet (untuk `xbps-install`)
- `git`. Gunakan `git clone`, **jangan** unduh ZIP, karena aset besar disimpan lewat Git LFS. `git-lfs` tidak perlu dipasang sebelum clone: `install` akan memasangnya lalu menjalankan `git lfs pull`.

## Instalasi

```sh
git clone https://github.com/T4n-Labs/xfce.git
cd xfce
./install
```

> `install` **menimpa** konfigurasi di `~/.config`. Config lama dibackup dulu ke `~/.config-backup-<timestamp>`.

Setelah selesai, **logout lalu login** kembali. Ini wajib agar touchpad dan grup `audio` aktif, dan membantu kalau ada tampilan yang belum berubah.

### Yang dilakukan `install`

1. **Backup** `xfce4`, `gtk-3.0`, `cava`, `conky`, `tilda`, `Thunar`, `autostart`, dan `mimeapps.list` ke `~/.config-backup-<timestamp>`.
2. **Install paket** (lihat tabel di bawah) dan `git-lfs`, lalu `git lfs pull` untuk mengunduh aset.
3. **Deploy aset** ke sistem:

   | Sumber | Tujuan |
   |---|---|
   | `assets/fonts/*.zip` | `/usr/share/fonts/<nama>/` |
   | `assets/themes/*.tar.xz` | `/usr/share/themes/` |
   | `assets/icons/*.tar.xz` | `/usr/share/icons/` |
   | `assets/wallpapers/*` | `/usr/share/backgrounds/t4n-os/` |

   Cache font diperbarui dengan `fc-cache`.
4. **Konfigurasi sistem**: semua `system/*.conf` disalin ke `/etc/X11/xorg.conf.d/`.
5. **Audio dan mikrofon**: menambahkan user ke grup `audio`, mengaktifkan capture ALSA, dan unmute mic default lewat `pactl` (80%) kalau sound server sedang berjalan.
6. **Deploy dotfiles**: isi `config/` disalin ke `~/.config`.
7. **Cek launcher panel**: memberi peringatan kalau aplikasi yang dipakai sebuah launcher belum terpasang.
8. **Bookmark Thunar** dibuat ulang dari folder yang ada di home (Desktop, Documents, Downloads, dst.).
9. **Wallpaper** `desert.jpg` diterapkan ke semua monitor yang terdeteksi.
10. **Auto-scaling HiDPI** berdasarkan lebar layar:

    | Lebar layar | Scaling | DPI |
    |---|---|---|
    | ≥ 3840 px | 2 | 192 |
    | ≥ 2560 px | 1 | 120 |
    | di bawahnya | 1 | 96 |

11. **Restart** `xfsettingsd` dan `xfce4-panel` agar config terbaca.

### Paket yang dipasang

| Kategori | Paket |
|---|---|
| Tampilan dan aplikasi | `conky` `tilda` `cava` `xfce4-whiskermenu-plugin` `unzip` |
| Panel dan shortcut | `xfce4-pulseaudio-plugin` `xfce4-screenshooter` `xfce4-taskmanager` |
| Audio | `alsa-utils` `pavucontrol` |
| Input | `xf86-input-libinput` |
| Aset | `git-lfs` |

Paket tambahan dipasang satu per satu. Kalau ada yang gagal, `install` hanya memberi peringatan dan tetap melanjutkan.

## Struktur repo

```
xfce/
├── assets/
│   ├── fonts/            JetBrainsMono.zip, RobotoMono.zip
│   ├── icons/            01-Tela.tar.xz
│   ├── themes/           Ant-Nebula.tar.xz
│   └── wallpapers/       desert.jpg, triangle-void.png, void1.png, void2.png
├── config/               disalin ke ~/.config
│   ├── autostart/        conky.desktop
│   ├── cava/             config, shaders/, themes/
│   ├── conky/            conky.conf
│   ├── gtk-3.0/          gtk.css, settings.ini
│   ├── Thunar/           accels.scm, uca.xml
│   ├── tilda/            config_0
│   ├── xfce4/
│   │   ├── desktop/      accels.scm
│   │   ├── panel/        launcher-29 ... launcher-33
│   │   ├── terminal/     terminalrc
│   │   └── xfconf/xfce-perchannel-xml/   *.xml (panel, xfwm4, xsettings, shortcut, dll.)
│   └── mimeapps.list
├── system/               30-touchpad.conf -> /etc/X11/xorg.conf.d/
├── clone                 salin config dari sistem ke repo (kebalikan install)
├── install               pasang semuanya ke sistem
├── LICENSE
├── Note.md
└── README.md
```

## Shortcut kustom

| Tombol | Aksi |
|---|---|
| `Super` | Whisker Menu |
| `Super` + `E` | Thunar |
| `Ctrl` + `Alt` + `T` | Terminal |
| `Ctrl` + `Alt` + `L` | Kunci layar |
| `Ctrl` + `Alt` + `Delete` | Logout |
| `Ctrl` + `Shift` + `Esc` | Task Manager |
| `Ctrl` + `Alt` + `Esc` | `xkill` |
| `Shift` + `Super` + `S` | Screenshot |
| `XF86AudioMicMute` | Toggle mute mikrofon |

Shortcut window manager (pindah workspace dengan `Ctrl` + `F1`–`F12`, tiling dengan `Super` + numpad, dst.) mengikuti bawaan XFCE. Ada 5 workspace.

## Menyimpan perubahan (`clone`)

Setelah mengubah tampilan lewat GUI, simpan ke repo dengan `clone`:

```sh
./clone -n        # dry-run: lihat dulu apa yang akan dilakukan
./clone           # salin ~/.config -> config/
git diff config   # periksa hasilnya
git add config && git commit -m "Update XFCE config" && git push
```

`clone` menyalin folder yang terdaftar di variabel `ITEMS`, membuang file yang spesifik mesin (wallpaper per monitor, layout monitor, bookmark, sesi), dan memperingatkan kalau ada kata yang mungkin sensitif seperti `password` atau `token`. Item lain bisa ditambahkan untuk sekali jalan, misalnya `./clone picom`. Jalankan `./clone -h` untuk opsi lengkap.

Repo ini publik, jadi selalu cek `git diff config` sebelum commit.

## Menambah aset sendiri

Taruh file sesuai format yang dibaca `install`:

| Jenis | Lokasi | Format |
|---|---|---|
| Font | `assets/fonts/<nama>.zip` | zip |
| Tema | `assets/themes/<nama>.tar.xz` | tar.xz |
| Ikon | `assets/icons/<nama>.tar.xz` | tar.xz |
| Wallpaper | `assets/wallpapers/` | gambar apa saja |

Pastikan file besar tercatat di Git LFS:

```sh
git lfs track "assets/**/*.zip" "assets/**/*.tar.xz"
git add .gitattributes
```

## Troubleshooting

**`unzip` atau `tar` gagal saat deploy aset.** Repo kemungkinan terunduh tanpa file LFS (misalnya dari ZIP). Jalankan `git lfs pull` di dalam repo, lalu ulangi `./install`.

**Tampilan belum berubah.** Logout lalu login. Kalau masih sama, jalankan `xfsettingsd --replace &` dan `xfce4-panel -r`.

**Touchpad tidak berubah.** Pastikan `/etc/X11/xorg.conf.d/30-touchpad.conf` ada dan `xf86-input-libinput` terpasang, lalu logout/login atau reboot.

**Mikrofon tidak terdengar.**
- Buka `pavucontrol`, tab *Input Devices*, dan pastikan mic tidak mute.
- Cek perangkat dengan `arecord -l` dan `pactl list short sources`.
- Kalau `arecord -l` kosong di laptop Intel, kemungkinan perlu paket `sof-firmware`.

**Ada launcher panel yang kosong atau muncul `[WARNING]` saat install.** Aplikasi yang dirujuk launcher belum terpasang. Pasang aplikasinya atau hapus launcher dari panel.

**Kembali ke config lama.** Backup ada di `~/.config-backup-<timestamp>`:

```sh
cp -r ~/.config-backup-<timestamp>/. ~/.config/
```

## Lisensi

MIT. Lihat berkas [LICENSE](LICENSE).

---

Bagian dari [T4n Labs](https://github.com/T4n-Labs).