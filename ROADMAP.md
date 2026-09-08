# ROADMAP — Biosecurity Research Analytics Platform

Послідовність спрінтів для соло-розробки в режимі part-time (орієнтовно ~1 тиждень на спрінт, з допомогою Claude Code). Кожен спрінт спирається на результат попереднього — не варто починати ML-спрінт, поки немає стабільного джерела синтетичних даних і QC.

Це орієнтир для планування, а не жорсткий контракт: спрінти можна зсувати, але порядок залежностей (Data → ML → Backend → Frontend → DevOps) міняти не варто, оскільки кожен наступний шар технічно спирається на попередній.

## Спринт 0 — Setup та джерела синтетичних даних
**Мета:** закласти легальний, задокументований фундамент даних, без якого жоден наступний крок не можна легітимно почати.
- [data/TODO_sources_licensing.md](data/TODO_sources_licensing.md) — усі P0-пункти (вибір датасету, генератор синтетичних зразків, заборонені категорії, DATA_SOURCES.md, ліцензії)
- Базовий каркас репозиторію (не описаний окремим TODO-файлом): структура папок backend/frontend/ml, README-заглушка
**Тривалість:** ~1 тиждень

## Спринт 1 — Ingestion + Quality Control
**Мета:** отримати робочий, провалідований потік прийому зразків від сирого payload до QC-звіту.
- [data/TODO_ingestion_pipeline.md](data/TODO_ingestion_pipeline.md) — P0/P1 пункти
- [data/TODO_quality_control.md](data/TODO_quality_control.md) — P0/P1 пункти
**Тривалість:** ~1 тиждень

## Спринт 2 — Feature extraction + класифікація
**Мета:** перетворити провалідовані зразки на вектори ознак і отримати перший робочий baseline-класифікатор.
- [data/TODO_feature_extraction.md](data/TODO_feature_extraction.md) — усі P0-пункти
- [ml/TODO_classification.md](ml/TODO_classification.md) — P0-пункти (baseline-модель, split, тренування, базові метрики)
**Тривалість:** ~1 тиждень

## Спринт 3 — Anomaly detection + довіра/валідація
**Мета:** додати виявлення аномалій (Isolation Forest як основний шлях, Autoencoder як порівняльний) та шар confidence/traceability поверх класифікації.
- [ml/TODO_anomaly_isolation_forest.md](ml/TODO_anomaly_isolation_forest.md) — усі P0-пункти
- [ml/TODO_anomaly_autoencoder.md](ml/TODO_anomaly_autoencoder.md) — P1-пункти (за наявності часу; не блокує наступний спрінт)
- [ml/TODO_confidence_validation.md](ml/TODO_confidence_validation.md) — P0/P1 пункти
**Тривалість:** ~1 тиждень

## Спринт 4 — Реєстр моделей, звітність і відтворюваність
**Мета:** зробити результати ML-етапів версійованими, трасованими та придатними для генерації reproducible-звіту з model card.
- [ml/TODO_model_registry.md](ml/TODO_model_registry.md) — усі P0-пункти
- [ml/TODO_reporting_reproducibility.md](ml/TODO_reporting_reproducibility.md) — усі P0-пункти
**Тривалість:** ~1 тиждень

## Спринт 5 — Backend: API та оркестрація пайплайну
**Мета:** обʼєднати всі попередні модулі (data + ML) у наскрізний асинхронний пайплайн з тонким REST API поверх нього.
- [backend/TODO_api_design.md](backend/TODO_api_design.md) — усі P0-пункти
- [backend/TODO_pipeline_orchestration.md](backend/TODO_pipeline_orchestration.md) — усі P0-пункти
- [backend/TODO_versioning_traceability.md](backend/TODO_versioning_traceability.md) — P0-пункти
- [backend/TODO_testing.md](backend/TODO_testing.md) — усі P0-пункти (паралельно з розробкою, не в кінці)
- [backend/TODO_logging_observability.md](backend/TODO_logging_observability.md) — P0-пункт (заборона логування сирих даних)
**Тривалість:** ~1.5 тижня

## Спринт 6 — Frontend: дашборд науковця та дисклеймери
**Мета:** дати науковцю робочий UI для подання зразків, перегляду статусу/звіту, з обов'язковими дисклеймерами на кожному кроці.
- [frontend/TODO_ui_components.md](frontend/TODO_ui_components.md) — P0-пункти
- [frontend/TODO_pages_flows.md](frontend/TODO_pages_flows.md) — P0-пункти
- [frontend/TODO_state_data_layer.md](frontend/TODO_state_data_layer.md) — P0-пункти
- [frontend/TODO_disclaimers_compliance.md](frontend/TODO_disclaimers_compliance.md) — усі P0-пункти (не відкладати — це частина MVP, а не полірування)
- [frontend/TODO_testing.md](frontend/TODO_testing.md) — P0-пункти (E2E smoke + E2E disclaimer)
**Тривалість:** ~1.5 тижня

## Спринт 7 — DevOps: контейнеризація, CI/CD та деплой з synthetic-only гарантіями
**Мета:** зробити систему відтворювано розгортуваною, з автоматизованими перевірками та публічним demo, що технічно не може прийняти нічого, крім синтетичних даних.
- [devops/TODO_containerization.md](devops/TODO_containerization.md) — P0-пункти
- [devops/TODO_cicd.md](devops/TODO_cicd.md) — P0/P1 пункти
- [devops/TODO_infrastructure_deployment.md](devops/TODO_infrastructure_deployment.md) — усі P0-пункти (synthetic-only гарантія, pre-release checklist)
- [devops/TODO_model_versioning_registry.md](devops/TODO_model_versioning_registry.md) — P1-пункти
- [devops/TODO_monitoring_observability.md](devops/TODO_monitoring_observability.md) — P1-пункти
**Тривалість:** ~1 тиждень

## Після MVP (P2 backlog)
Усі пункти з приорітетом **P2** у кожній категорії (полірування UI, порівняння зразків, розширений моніторинг, Autoencoder-порівняння в повному обсязі) — виконуються ітеративно після того, як наскрізний MVP-флоу (submission → QC → ML → confidence → report → UI з disclaimer) стабільно працює.

### Примітка щодо захисної рамки
Кожен спрінт зберігає ті самі обмеження, що й проєкт у цілому: лише публічні/синтетичні дані, ніяких реальних патогенних/клінічних даних, явні дисклеймери на кожному етапі, де результати показуються людині. Спринт 0 і Спринт 7 містять "ворота" (gate) цієї політики — джерела на вході, pre-release checklist на виході.
