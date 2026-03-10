# MekoSort 🚀

**Lightning-fast Photo Culling & Sorting Engine.**

![MekoSort App](<img width="895" height="661" alt="Screenshot 2026-03-09 124531" src="https://github.com/user-attachments/assets/b938b127-639f-40b4-8a6c-e04b027057bc" />
)

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
