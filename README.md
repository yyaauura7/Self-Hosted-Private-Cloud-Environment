# Self-Hosted-Private-Cloud-Environment
Описание: Инфраструктура приватного облака на базе Nextcloud, развернутая с использованием Docker Compose, с настроенным обратным прокси и автоматическим выпуском SSL-сертификатов.

Архитектура:

Frontend / Reverse Proxy: Nginx (настроен на хосте для маршрутизации и терминации SSL).

Security: Let's Encrypt + Certbot для автоматического HTTPS. UFW (файрвол) настроен на блокировку всего, кроме 22, 80, и 443 портов.

Application: Nextcloud (в Docker).

Database: MariaDB (в Docker).

Storage: Использование Docker Volumes для персистентного хранения данных базы и приложения (Stateful).

Схема:  Internet -> UFW -> Nginx (80 -> 301 Redirect to 443) -> Nginx (443 SSL) -> Docker (8080) -> Nextcloud).
