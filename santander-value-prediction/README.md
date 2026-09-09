# Santander Value Prediction

Проект по регрессии на разреженных табличных данных из соревнования [Santander Value Prediction Challenge](https://www.kaggle.com/competitions/santander-value-prediction-challenge). Цель — предсказать непрерывную целевую величину по 4 991 анонимизированному признаку.

## Что сделано

- исследованы распределение таргета, разреженность и информативность признаков;
- построены 9 агрегатов по строке и отобраны 600 наиболее активных исходных признаков;
- применено преобразование `signed_log1p`, итоговая матрица содержит 609 признаков;
- Ridge, ExtraTrees, RandomForest, HistGradientBoosting и LightGBM сравниваются на **одинаковых признаках и одинаковых фолдах**;
- параметры подбираются на 3-fold CV, финальное сравнение проводится по 5-fold OOF CV;
- лучший вариант выбирается только по CV и затем переобучается на всём train;
- создаются воспроизводимые артефакты: таблицы сравнения, важность признаков, сводка запуска и submission.

## Результат

Лучшим вариантом стал weighted blend трёх моделей:

| Модель | Вес |
|---|---:|
| ExtraTrees | 0.3337 |
| RandomForest | 0.3336 |
| LightGBM | 0.3327 |

**OOF CV RMSLE: 1.336892.**

Сравнение на едином наборе признаков:

| Вариант | OOF CV RMSLE |
|---|---:|
| Weighted blend | 1.336892 |
| ExtraTrees | 1.341706 |
| RandomForest | 1.342065 |
| LightGBM | 1.345767 |
| HistGradientBoosting | 1.350266 |
| Ridge | 1.431552 |

Kaggle test не использовался для выбора модели. После выбора компоненты ансамбля переобучены на всех 4 459 строках train.

## Структура

```text
.
├── artifacts/
│   ├── feature_importance.csv
│   ├── hyperparameter_search_results.csv
│   ├── model_selection.csv
│   ├── run_summary.json
│   └── submission_final.csv
├── santander_value_prediction.ipynb
├── requirements.txt
└── README.md
```

## Данные

Скачайте данные со [страницы соревнования](https://www.kaggle.com/competitions/santander-value-prediction-challenge/data) и поместите файлы так:

```text
data/santander-value-prediction-challenge/
├── train.csv
├── test.csv
└── sample_submission.csv
```

Также можно указать каталог через переменную окружения `SANTANDER_DATA_PATH`.

## Запуск

```powershell
git clone --branch project/santander-value-prediction https://github.com/Streeelaa/ml_dz1.git santander-value-prediction
cd santander-value-prediction
python -m pip install -r requirements.txt
python -m jupyter lab santander_value_prediction.ipynb
```

Ноутбук уже содержит выполненные ячейки и зафиксированный результат последнего запуска.
