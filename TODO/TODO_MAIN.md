# TODO — Biosecurity Research Analytics Platform

## Опис проєкту

Дослідницька платформа для аналізу біологічних/молекулярних зразків та
автоматичного формування ML-based гіпотез для лабораторії: прийом даних
зразка → контроль якості → вилучення ознак → ML-аналіз → класифікація/пошук
аномалій → оцінка довіри → дашборд для науковця → відтворюваний звіт.

**Важливо:** проєкт працює виключно з публічними або синтетичними/навчальними
датасетами. Це аналітична/дефенсивна дослідницька система, а НЕ інструмент
для проєктування, оптимізації чи створення небезпечних патогенів або токсинів.
Мета — продемонструвати вміння будувати end-to-end data/ML pipeline для
біологічних даних, не більше.

**Мета:** показати здатність будувати повноцінну end-to-end систему
(ingestion → QC → ML → reporting), що є найближчим аналогом реального
research-tooling workflow в R&D-командах.

**Статус:** 🔴 Не розпочато (фінальний, найскладніший проєкт у серії)

**План виконання:** [ROADMAP.md](ROADMAP.md) — 8 послідовних спрінтів (0-7) від джерел даних до деплою.

## Мовна політика

Продукт (UI, README, код, коментарі, API-документація, дисклеймери) —
англійською мовою як основною. Українська — друга мова (i18n locale),
опційна. TODO-плани залишаються українською для зручності автора.

## Категорії

## Data
- [Джерела даних та ліцензування](data/TODO_sources_licensing.md)
- [Ingestion pipeline](data/TODO_ingestion_pipeline.md)
- [Quality Control](data/TODO_quality_control.md)
- [Feature extraction](data/TODO_feature_extraction.md)

## ML
- [Класифікація](ml/TODO_classification.md)
- [Виявлення аномалій — Isolation Forest](ml/TODO_anomaly_isolation_forest.md)
- [Виявлення аномалій — Autoencoder](ml/TODO_anomaly_autoencoder.md)
- [Довіра та валідація](ml/TODO_confidence_validation.md)
- [Звітність та відтворюваність](ml/TODO_reporting_reproducibility.md)
- [Реєстр моделей та версіонування](ml/TODO_model_registry.md)

## Backend
- [API Design](backend/TODO_api_design.md)
- [Оркестрація пайплайну](backend/TODO_pipeline_orchestration.md)
- [Версіонування та трасованість](backend/TODO_versioning_traceability.md)
- [Тестування](backend/TODO_testing.md)
- [Логування та спостережуваність](backend/TODO_logging_observability.md)

## Frontend
- [UI компоненти](frontend/TODO_ui_components.md)
- [Сторінки та флоу](frontend/TODO_pages_flows.md)
- [State та data layer](frontend/TODO_state_data_layer.md)
- [Дисклеймери та відповідність призначенню](frontend/TODO_disclaimers_compliance.md)
- [Тестування](frontend/TODO_testing.md)
- [Layout дашборду](frontend/TODO_dashboard_layout.md)
- [Візуалізація даних](frontend/TODO_data_visualization.md)
- [i18n та локалізація](frontend/TODO_i18n_localization.md)

## DevOps
- [Контейнеризація](devops/TODO_containerization.md)
- [CI/CD](devops/TODO_cicd.md)
- [Інфраструктура та деплой](devops/TODO_infrastructure_deployment.md)
- [Версіонування моделей у деплої](devops/TODO_model_versioning_registry.md)
- [Моніторинг та спостережуваність](devops/TODO_monitoring_observability.md)

## Загальний прогрес

| Категорія | Виконано | Всього |
|---|---|---|
| Data | 0 | 34 |
| ML | 0 | 46 |
| Backend | 0 | 38 |
| Frontend | 0 | 56 |
| DevOps | 0 | 28 |
| **Разом** | **0** | **202** |

### Примітки
- Тільки публічні/синтетичні датасети — жодних реальних лабораторних, персональних чи чутливих даних, на будь-якому етапі (джерела, тести, CI, публічний demo).
- Позиціювати як "research/educational analytics tool", з чіткими обмеженнями в README, model card кожної моделі та disclaimer на кожній сторінці результатів.
- Це узагальнення напрацювань усіх попередніх 4 проєктів (data pipeline, ML, backend, dashboard) в один end-to-end продукт.
- Кожен новий TODO-файл категорії тримає фокус на одній підтемі — це полегшує відстеження прогресу та планування спрінтів по вужчих ділянках роботи.
- Кожне завдання позначене пріоритетом (**P0** критичний шлях, **P1** важливо для MVP, **P2** полірування) та орієнтовною оцінкою часу — деталі й порядок виконання див. у [ROADMAP.md](ROADMAP.md).
- Розділ ML розбито на `TODO_anomaly_isolation_forest.md` та `TODO_anomaly_autoencoder.md` (замість колишнього єдиного `TODO_anomaly_detection.md`) — Isolation Forest є основним (P0) підходом, Autoencoder — порівняльним (P1/P2).
