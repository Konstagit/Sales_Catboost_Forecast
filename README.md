# Модель прогнозирования продаж

Этот проект направлен на прогнозирование продаж с обязательным услвоием учета дня недели и акций.

## Структура Проекта

- **code.ipynb**: Jupyter notebook, содержащий весь рабочий процесс для предобработки данных, создания признаков, обучения модели и оценки.
- **requirements.txt**: Список необходимых Python библиотек и их версий.
- **sales_raw.csv**: Исходный файл данных о продажах.
- **discounts_raw.csv**: Исходный файл данных о скидках.
- **predictions.csv**: Файл с  прогнозами продаж на месяц вперед

## Структура Данных

### sales_raw.csv

- **item_id**: Идентификатор товара
- **date**: Дата продажи
- **qnty**: Количество проданных единиц

### discounts_raw.csv

- **item_id**: Идентификатор товара
- **date_start**: Начальная дата акции
- **date_end**: Конечная дата акции
- **promo_typeCode**: Код типа акции
- **sale_price_before_promo**: Цена до начала акции
- **sale_price_time_promo**: Цена во время акции

## Значимость работы
В работе были проведены эксперименты, по результатам которых была выбрана модель CatBoostRegressor. В работе четко и последовательно объясняются все решения, выбор модели, работа с данными, особенности построения прогноза.
Это позволит шаг за шагом проследить ход мыслей и оценить выбор инструментария и решений, использованных для выполнения этой задачи.

## Работа с CatBoost

Для улучшения качества прогнозирования использовалась модель `CatBoostRegressor`, которая эффективно обрабатывает в том числе с категориальными признаками. Модель была обучена на исторических данных, включая информацию о скидках и временных характеристиках. Основные этапы включали:

1. **Предобработка данных**: Объединение данных о продажах и скидках, обработка пропусков, создание новых признаков.
2. **Обучение модели**: Настройка и обучение `CatBoostRegressor` на подготовленных данных.
3. **Настройка гиперпараметров с Optuna**: Настройка и обучение `CatBoostRegressor` на подготовленных данных.
4. **Оценка модели**: Проверка результатов модели с использованием метрик RMSE и MAE.
5. **Прогнозирование**: Генерация прогнозов на январь 2024 года на основе исторических данных.

В итоге был сформирован файл predictions.csv с разделителем ';'.В нем 3 столбца:
- **date**: Дата продажи
- **item_id**: Идентификатор товара
- **prediction**: Предсказание проданных единиц

## Использование

### 1. Клонирование репозитория
```bash
git clone https://github.com/beltelml/test.git
cd test
```

### 2. Установка зависимостей
Убедитесь, что файлы `sales_raw.csv` и `discounts_raw.csv` находятся в каталоге проекта, затем установите необходимые библиотеки:
```bash
pip install -r requirements.txt
```

### 3. Запуск Jupyter notebook
Откройте Jupyter notebook и выполните все ячейки в `code.ipynb`:
```bash
python - m notebook code.ipynb
```

### Предобработка данных
Следуйте шагам в ноутбуке для обработки данных, включая объединение данных о продажах и скидках, создание признаков, и обработку пропусков.

### Обучение и оценка модели
Обучите модель `CatBoostRegressor` на подготовленных данных и оцените её с помощью метрик RMSE и MAE.

### Прогнозирование
Сгенерируйте прогнозы на январь 2024 года, используя обученную модель.

## Заключение

Проект демонстрирует важность создания признаков и обработки временных рядов для точного прогнозирования продаж. Учитывая эффекты акций и другие релевантные факторы, модель стремится предоставить надежные прогнозы, которые могут помочь в принятии бизнес-решений.

---

Если у вас есть вопросы или нужна дополнительная помощь, не стесняйтесь обращаться.