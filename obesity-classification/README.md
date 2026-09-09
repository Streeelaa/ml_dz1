# Obesity Level Classification

Проект по классификации семи уровней массы тела на основе антропометрических показателей, пищевых привычек, физической активности и образа жизни.

## Данные

- источник: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/544/estimation+of+obesity+levels+based+on+eating+habits+and+physical+condition);
- 2 087 наблюдений после удаления полных дубликатов;
- 7 достаточно сбалансированных целевых классов;
- числовые и категориальные признаки;
- часть исходных записей создана синтетически.

## Что сделано

- исследованы распределения, корреляции, пропуски и баланс классов;
- предобработка собрана в `ColumnTransformer` и `Pipeline` без утечки между фолдами;
- сравнены Logistic Regression, Decision Tree и Random Forest;
- выполнены 5-fold CV и подбор гиперпараметров;
- использован `SelectKBest` для отбора признаков;
- проверены семь заранее сформулированных гипотез;
- построены classification report и confusion matrix.

## Результат

Лучшей моделью стал настроенный **Random Forest**:

| Метрика | Значение |
|---|---:|
| Test accuracy | 0.9785 |
| Test macro-F1 | 0.9778 |
| 5-fold CV macro-F1 | 0.9810 |

Подтвердились 6 из 7 исследовательских гипотез.

## Важное ограничение

Целевые классы тесно связаны с BMI, а BMI вычисляется из `Weight` и `Height`. Поэтому антропометрические признаки почти восстанавливают правило разметки и объясняют очень высокое качество. Этот результат полезен как исследование поведения моделей на датасете, но его нельзя трактовать как независимое медицинское предсказание по образу жизни.

## Структура

```text
.
├── data/
│   └── ObesityDataSet_raw_and_data_sinthetic.csv
├── obesity_level_classification.ipynb
├── requirements.txt
└── README.md
```

## Запуск

```powershell
git clone --branch project/obesity-level-classification https://github.com/Streeelaa/ml_dz1.git obesity-level-classification
cd obesity-level-classification
python -m pip install -r requirements.txt
python -m jupyter lab obesity_level_classification.ipynb
```

Ноутбук уже содержит выполненные ячейки и графики.
