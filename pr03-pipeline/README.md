# Практическая работа №3. Сборка пайплайна предобработки

Вариант: C

ФИО: Курбатов Максим CS-32

Датасет: Palmer Penguins (`penguins_size.csv`), источник — Kaggle
(parulpandey/palmer-archipelago-antarctica-penguin-data), тот же, что в ПР1 и ПР2.

## Что сделано

- Разбиение train/test (80/20, стратификация по виду) до любых вычислений статистик
- Собственный трансформер `IQRClipper` (BaseEstimator, TransformerMixin): обрезка выбросов
  по границам IQR, вычисляемым в fit только на train
- Общий пайплайн (ColumnTransformer): медиана → IQRClipper → StandardScaler для числовых,
  "unknown" → OneHotEncoder для категориального признака
- Два теста трансформера (assert в notebook)
- Замер производительности на синтетически увеличенной выборке (до 1 млн строк), указано узкое место