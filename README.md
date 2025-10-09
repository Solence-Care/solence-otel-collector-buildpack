# 📘 OpenTelemetry Collector Buildpack

This project define buildpack to run **OpenTelemetry Collector** using the official Docker image.

---

## 📂 Project Structure

```bash
 .
├── bin/detect  # Tells if the buildpack should be applied.
├── bin/compile # Installs everything needed for the runtime into the app’s build directory.
└── bin/release # Tells which process types to run by default.
```
