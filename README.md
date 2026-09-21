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

---

## ⚙️ Collector version

`bin/compile` installs the `otelcol-contrib` release named by **`OTELCOL_VERSION`**
(e.g. `v0.161.0`), and falls back to `v0.148.0` when the variable is unset.

Set it per app, in `terraform/{ci,staging,prod}/main.tf` of `solence-infra`, next
to `BUILDPACK_URL`. Terraform is the source of truth, so each environment states
the version it runs and a plain redeploy rebuilds that same version — an app
never moves to a new collector on its own.

To upgrade: bump `OTELCOL_VERSION` for one environment, redeploy that app, check
that logs and traces still reach OpenSearch, then do the next environment.

Releases: <https://github.com/open-telemetry/opentelemetry-collector-releases/releases>
