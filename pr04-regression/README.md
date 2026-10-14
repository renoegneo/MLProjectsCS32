# Практическая работа №4. Регрессионная модель

Вариант: C


Датасет: Palmer Penguins (`penguins_size.csv`), источник — Kaggle
(parulpandey/palmer-archipelago-antarctica-penguin-data). Целевая переменная — масса тела (`body_mass_g`).

## Что сделано

- Пайплайн предобработки из ПР3: медиана → IQRClipper → StandardScaler для числовых признаков,
  "unknown" → OneHotEncoder(drop="first") для пола
- Собственные MSE, градиент и градиентный спуск на NumPy (градиент проверен численно)
- Сравнение со scikit-learn LinearRegression на одних данных
- Исследование скорости обучения: 0.01, 0.1, 0.5, 0.8

## Результаты (test, 69 пингвинов)

| Метрика | Свой GD | scikit-learn |
|---|---|---|
| MAE, г | 266,3 | 266,3 |
| RMSE, г | 323,3 | 323,3 |
| R² | 0,843 | 0,843 |

Коэффициенты совпали с точностью до 0,11 г (кроме редкой категории sex_unknown, 1,1 г).
Подробные выводы и графики: `notebooks/regression.ipynb`.