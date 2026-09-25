# FinGuard AI — как запустить

```bash
cd python
pip install pandas numpy scikit-learn python-dateutil streamlit --break-system-packages

python3 1_generate_data.py      # генерирует data/*.csv
python3 2_financial_health.py   # Stage 1
python3 3_anomaly_detection.py  # Stage 2
python3 4_forecast.py           # Stage 3
python3 5_pd_model.py           # Stage 4 (PD)
python3 6_risk_engine.py        # финал -> data/final_reports.json

streamlit run 7_dashboard.py    # дашборд для демо
```

Порядок запуска важен (каждый скрипт читает CSV, созданный предыдущим).
Все скрипты уже протестированы и отработали end-to-end на синтетических данных.

## Что нужно вручную (Person 2)
1. Открыть kase.kz -> Раскрытие информации -> выбрать 2-3 эмитента ->
   скачать последние отчётности -> вписать реальные цифры в
   `python/1_generate_data.py`, список `REAL_KASE_COMPANIES`.
2. (опционально) Скачать UCI/Kaggle credit-датасет в `data/external_credit_dataset.csv`
   для `5_pd_model.py` (иначе используется честный fallback-режим).
3. Подобрать/проверить пороги и веса в `2_financial_health.py` (WEIGHTS)
   и `6_risk_engine.py` (OVERALL_WEIGHTS) — это бизнес-логика, не код.
