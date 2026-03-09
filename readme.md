# MekoSort 🚀

**Lightning-fast Photo Culling & Sorting Engine.**

![MekoSort App](https://via.placeholder.com/800x400.png?text=Upload+Screenshot+Aplikasi+Lu+Nanti+Kesini)

MekoSort is a professional desktop application engineered to solve the biggest bottleneck in a photographer's workflow: sorting through thousands of massive photo files. Built with a focus on absolute speed and zero-lag user experience.

Crafted by **Meko no Mori** - UI/UX & Software Agency.

## 📥 Download & Installation

1. Go to the [Releases](../../releases) tab.
2. Download `MekoSort Setup 1.0.0.exe`.
3. Run the installer and start sorting your photos instantly.
   _(Note: Windows SmartScreen might show an "Unknown Publisher" warning for indie developers. Click "More Info" -> "Run Anyway")._

---

## 🛠️ Under the Hood (Architecture & Engineering)

_For Tech Leads and Developers._

Building a desktop app that handles **6,000+ high-resolution images** simultaneously without crashing requires strict memory management and an optimized architecture.

**Tech Stack:** `Electron` | `React` | `TypeScript` | `Vite` | `TailwindCSS` | `Better-SQLite3`

### Key Engineering Challenges Solved:

1. **Zero-Lag Infinite Scroll:** Implemented DOM virtualization in React to render only the visible photos, preventing memory leaks and maintaining 60fps scrolling even with massive directories.
2. **State Persistence:** Integrated `Better-SQLite3` directly into the Electron Main Process. Every cull, label, and category change is immediately synced to a local `.db` file. If the app crashes or the PC shuts down, zero progress is lost.
3. **Non-Destructive OS Operations:** Leveraged Node.js `fs` module for lightning-fast file movements, executing physical file transfers only when the user explicitly hits "Execute".
4. **Keyboard-First Navigation:** Optimized event listeners for seamless, mouse-free culling using Arrow Keys (Navigation) and Numpad `[1-5]` (Categorization).

### Code Snippet: Safe Execution Engine

_(A glimpse into how MekoSort safely routes files at the OS level)_

```typescript
// Abstracted concept of the Culling Execution
async function executeCull(projectId, photoList) {
  try {
    db.transaction(() => {
      photoList.forEach((photo) => {
        if (photo.status === "APPROVED") {
          fs.renameSync(photo.sourcePath, photo.targetPath);
          db.updateStatus(photo.id, "MOVED");
        }
      });
    })();
  } catch (error) {
    logger.error("Execution halted to prevent data loss", error);
  }
}
```

### 📄 License

© 2026 Meko no Mori. All rights reserved. This is a proprietary commercial product. The source code is private.

### Langkah 3: Push ke GitHub (Public)

1. Buka GitHub lu di _browser_. Bikin repository baru, kasih nama **`MekoSort`**.
2. **WAJIB pilih opsi PUBLIC.** (Jangan centang _Add a README file_, biarin kosong).
3. Buka terminal di VSCode baru lu (yang folder `MekoSort-Release`), ketik perintah sakti ini:
   - `git init`
   - `git add README.md`
   - `git commit -m "Initial release documentation"`
   - `git branch -M main`
   - `git remote add origin <PASTE_LINK_REPO_PUBLIC_LU>`
   - `git push -u origin main`

### Langkah 4: Pajang Barangnya (.exe)

1. Pergi ke halaman repo `MekoSort` (Public) lu di GitHub.
2. Liat menu sebelah kanan, klik **Releases** -> **Create a new release**.
3. _Tag version_: ketik `v1.0.0`
4. _Release title_: ketik `MekoSort v1.0.0 - Initial Release`
5. **Drag & Drop** file `MekoSort Setup 1.0.0.exe` (yang udah lu bikin sebelumnya) ke kotak _Attach binaries by dropping them here_.
6. Klik **Publish release**.

---

Gass lakuin 4 langkah ini. Nanti kalau lu mau nambahin gambar logo atau _screenshot_ aplikasi lu ke dalem `README.md`, tinggal lu _edit_ file-nya nanti. Lapor ke gue kalau Etalase lu udah tayang dan file `.exe`-nya udah mejeng di _Releases_!
