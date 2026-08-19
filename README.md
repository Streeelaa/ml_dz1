# Machine Learning Projects

Два самостоятельных проекта по табличному машинному обучению: многоклассовая классификация и регрессия на разреженных анонимизированных данных. Каждый проект находится в отдельной ветке и содержит выполненный Jupyter Notebook, описание методологии, зависимости и зафиксированные результаты.

## Проекты

### 1. [Obesity Level Classification](https://github.com/Streeelaa/ml_dz1/tree/project/obesity-level-classification)

Классификация семи уровней массы тела по антропометрическим показателям и особенностям образа жизни.

- EDA и проверка семи исследовательских гипотез;
- preprocessing без утечки данных;
- Logistic Regression, Decision Tree и Random Forest;
- 5-fold CV, подбор гиперпараметров и SelectKBest;
- test macro-F1 лучшей модели: **0.9778**;
- отдельный разбор ограничения, связанного с разметкой классов по BMI.

```powershell
git clone --branch project/obesity-level-classification https://github.com/Streeelaa/ml_dz1.git obesity-level-classification
```

### 2. [Santander Value Prediction](https://github.com/Streeelaa/ml_dz1/tree/project/santander-value-prediction)

Регрессия на 4 991 разреженном анонимизированном признаке из Kaggle Santander Value Prediction Challenge.

- анализ разреженности и feature engineering;
- единая 609-мерная матрица для всех сравниваемых моделей;
- Ridge, ExtraTrees, RandomForest, HistGradientBoosting и LightGBM;
- выбор победителя исключительно по 5-fold OOF CV;
- полное переобучение выбранного weighted blend на train;
- OOF CV RMSLE: **1.336892**.

```powershell
git clone --branch project/santander-value-prediction https://github.com/Streeelaa/ml_dz1.git santander-value-prediction
```

## Навигация

| Проект | Тип задачи | Основная метрика | Ветка |
|---|---|---|---|
| Obesity Level Classification | Multiclass classification | Macro-F1 | [`project/obesity-level-classification`](https://github.com/Streeelaa/ml_dz1/tree/project/obesity-level-classification) |
| Santander Value Prediction | Regression | RMSLE | [`project/santander-value-prediction`](https://github.com/Streeelaa/ml_dz1/tree/project/santander-value-prediction) |

Подробные инструкции по данным и запуску находятся в README соответствующей ветки.
