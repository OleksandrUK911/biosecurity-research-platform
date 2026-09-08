# TODO — Контейнеризація (Biosecurity Research Platform)

## Dockerfile
- [ ] Dockerfile для backend, що включає залежності пайплайну оркестрації (ingestion → QC → ML → report) — **P0** | ~3h
- [ ] Dockerfile для frontend (multi-stage build, статичні файли) — **P0** | ~2h
- [ ] Мінімізація розміру образів (multi-stage build, виключення dev-залежностей) — **P2** | ~2h

## docker-compose
- [ ] `docker-compose.yml`: backend + frontend + postgres + worker — **P0** | ~3h
- [ ] Налаштування volumes для персистентного зберігання даних/моделей у dev-середовищі — **P1** | ~1h
- [ ] Змінні середовища для конфігурації сервісів (`.env.example`) — **P1** | ~1h

### Примітки
- Перед формуванням образів перевірити, що жодні "сирі" зовнішні датасети не копіюються в образ — лише скрипти для їх завантаження або синтетичні дані.

### Залежності
- Залежить від наявності робочого backend (`backend/`) та frontend (`frontend/`) коду.
- Блокує `devops/TODO_cicd.md` (build/smoke-test workflow) та `devops/TODO_infrastructure_deployment.md`.
