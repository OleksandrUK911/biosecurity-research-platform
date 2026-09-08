# TODO — API Design (Biosecurity Research Platform)

## Основні ендпоінти
- [ ] `POST /samples` — прийом нового зразка (валідація payload, повернення `sample_id`) — **P0** | ~3h
- [ ] `GET /samples/{id}/status` — статус пайплайну (queued → ingesting → qc → features → ml → report → done/failed) — **P0** | ~2h
- [ ] `GET /samples/{id}/report` — відтворюваний звіт аналізу (JSON, з опцією PDF/HTML) — **P0** | ~3h
- [ ] `GET /samples` — список зразків з фільтрацією/пагінацією — **P1** | ~2h

## Допоміжні ендпоінти
- [ ] `GET /models` — список доступних версій моделей та їх model card — **P1** | ~2h
- [ ] `GET /health` — health-check ендпоінт для моніторингу — **P1** | ~1h

## Якість API
- [ ] Валідація вхідних даних (схема, обов'язкові поля) на рівні API-шару — **P0** | ~2h
- [ ] Узгоджений формат помилок (error envelope з кодом та описом) — **P1** | ~2h
- [ ] OpenAPI/Swagger специфікація для всіх ендпоінтів — **P1** | ~2h
- [ ] API-документація та тексти помилок (error envelope) англійською мовою як основною (продукт англомовний, українська — опційна локаль) — **P1** | ~1h

### Примітки
- API навмисно "тонке" над пайплайном: логіка обробки живе в модулях orchestration/ML, а не в контролерах — це спрощує тестування та повторне використання.

### Залежності
- Залежить від `backend/TODO_pipeline_orchestration.md` (статуси і стани, що віддає `/status`) та `ml/TODO_reporting_reproducibility.md` (формат `/report`).
- Контракт ендпоінтів напряму споживається `frontend/TODO_state_data_layer.md` (типізований API-клієнт).
