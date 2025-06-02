# Lab 11 – Multiarch Docker Pipeline

Ten projekt buduje obraz kontenera w architekturze `linux/amd64` i `linux/arm64` z użyciem GitHub Actions.

## Funkcjonalność:
- 🔒 Skanowanie CVE przy użyciu Trivy
- 🧠 Cache warstw budowy w DockerHub (eksporter `registry`, `mode=max`)
- ⛔ Publikacja tylko przy braku HIGH/CRITICAL CVEs

## Obraz:
`ghcr.io/<login>/lab11-multiarch-ci:latest`
