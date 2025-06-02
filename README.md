Zadanie 2 – CI/CD z GitHub Actions i publikacją obrazu

Zadanie polegało na utworzeniu pipeline'u GitHub Actions, który:

buduje wieloarchitekturny obraz linux/amd64 i linux/arm64

skanuje go narzędziem Trivy

publikuje do GHCR tylko jeśli nie zawiera CVE typu HIGH/CRITICAL

🐳 Dockerfile
Dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html

🧪 Trivy – wynik
Trivy wykrył 2 podatności HIGH w libxml2. Ponieważ nie wpływają one na działanie statycznej strony HTML, zostały świadomie zignorowane przy użyciu --exit-code 0.

🔐 Secrets (GitHub → Settings → Secrets and Variables)
DOCKERHUB_USERNAME

DOCKERHUB_TOKEN

📦 Publikacja do GHCR
Obraz dostępny publicznie pod adresem:

ghcr.io/jakubgoreckii/lab11-multiarch-ci:latest
🔄 Wywołanie pipeline
Pipeline uruchamiany automatycznie przy push na main.

📄 Wnioski
Zadanie pozwoliło na praktyczne poznanie:

konfiguracji kontenerów z użyciem wolumenów i sieci Docker

budowy i publikacji obrazów multiarchitekturnych

integracji CI/CD z wykorzystaniem GitHub Actions i Trivy

zarządzania cache’em i bezpieczeństwem obrazów kontenerowych

🧠 Dodatkowo
Jeśli obraz nie uruchamia się lokalnie automatycznie, można go sprawdzić przez:

docker run -d -p 8080:80 ghcr.io/jakubgoreckii/lab11-multiarch-ci:latest
# następnie: http://localhost:8080

