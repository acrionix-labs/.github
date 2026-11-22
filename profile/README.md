<p align="left">
  <a href="https://acrionix.cloud">
    <img src="https://acrionix.cloud/avatar.svg" width="56" height="56" alt="Acrionix" />
  </a>
</p>

# Acrionix

**AI-native AOSP, Embedded Android, and Linux Kernel debugging platform.**

Acrionix ingests runtime `logcat`, `dmesg`, `tombstones`, and SELinux (`avc: denied`) logs, correlates them directly against your device tree (`BoardConfig.mk`, `sepolicy/*.te`, `init.rc`, VINTF manifests), and synthesizes minimal, least-privilege `git diff` patches in seconds.

[Website](https://acrionix.cloud) · [Live Sandbox](https://acrionix.cloud/#sandbox) · [Documentation](https://docs.acrionix.net) · [founder@acrionix.cloud](mailto:founder@acrionix.cloud)

---

### What we build

- **Least-Privilege SELinux Synthesizer** - Converts raw `avc: denied` audits into scoped `.te` rules and `file_contexts` entries validated against AOSP `neverallow` rules.
- **HIDL & AIDL Compatibility Resolver** - Detects missing HAL entries and generates compliant `manifest.xml` and `compatibility_matrix.xml` patches.
- **Native Crash & Tombstone Triage** - Symbolicates C/C++ stack traces, `init` service exit codes, and missing firmware blobs across vendor partitions.
- **Hardware-in-the-Loop CI Integration** - Opens automated Pull Requests whenever nightly AOSP 13-17 or GKI kernel builds fail on test rigs.

### Quickstart

```bash
pip install acrionix-cli
acrionix watch --adb --tree ./device/oem/sm8650
```

### Repositories

- [`acrionix-web`](https://github.com/acrionix-labs/acrionix-web) - Landing page, interactive Log-to-Patch sandbox, documentation portal (`docs.acrionix.net`), and Cloudflare Worker edge runtime.
- `acrionix-cli` *(in active development)* - Python CLI for live ADB streaming, offline log triage, and unified `.patch` synthesis.
