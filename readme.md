# MekoSort v2.0.0 - The Rust Revolution 🦀

**Lightning-fast Photo Culling & Sorting Engine.**

MekoSort adalah aplikasi desktop profesional yang dirancang untuk mengatasi hambatan terbesar fotografer: menyortir ribuan file RAW berukuran besar tanpa lag.

## 🛠️ Re-Engineered with Rust
Di versi 2.0.0, kami membuang arsitektur lama dan membangun ulang inti aplikasi menggunakan **Tauri & Rust**. Hasilnya? Penggunaan memori turun hingga 80% dan kecepatan render naik 5x lipat.

### 📥 Download v2.0.0
1. Buka tab [Releases](../../releases).
2. Unduh `MekoSort_v2.0.0_x64.msi`.
3. Nikmati kecepatan sortir foto yang sesungguhnya.

---

## 🛠️ Arsitektur & Rekayasa (v2.0.0)

**Tech Stack:** `Tauri` | `Rust` | `React` | `TypeScript` | `Vite` | `TailwindCSS`

### Key Engineering Challenges Solved:
1. **Rust-Powered Processing:** Pemrosesan metadata file RAW (.arw, .cr2, .nef) dilakukan langsung di tingkat sistem via Rust, menjamin nol latensi saat navigasi.
2. **Native OS Operations:** Menggunakan `std::fs` Rust untuk manajemen file yang jauh lebih aman dan cepat dibanding modul Node.js konvensional.
3. **Memory Safety:** Arsitektur Tauri memastikan aplikasi tidak memakan RAM berlebih seperti browser, menjaga PC tetap dingin saat memproses direktori raksasa.

### 📄 License
© 2026 Meko no Mori. Proprietary software.
