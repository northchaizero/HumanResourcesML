# Оптимизация управления персоналом для HR сервиса.

## Постановка задачи
В данном проекте последовательно выполнены 2 задачи:

**Оценка индекса удволетворённости сотрудников (регрессия)**

    Цель - SMOTE <= 15

**Предсказание ухода сотрудника из компании (бинарная классификация)**

    Цель - ROC-AUC >= 0.91

## Задача первая
### Выполненные шаги:
1. Загрузка и первичный анализ данных
2. Предобработка данных
3. Исследовательский анализ
4. Корреляционный анализ
5. Подготовка пайплайна предобработки и обучения
6. Поиск лучших моделей и гиперпараметров с помощью RandomizedSearchCV
### Итоговые выводы по задаче 1
Лучшей моделью с метрикой SMOTE = 11.26 является GradientBoostingRegressor, гиперпараметры можно найти в тетрадке (вкладка 'Обучение моделей' в задаче 1).

## Задача вторая
### Выполненные шаги:
1. Загрузка и первичный анализ данных
2. Предобработка данных
3. Исследовательский анализ
4. Корреляционный анализ
5. Составление портрета уволившегося сотрудника по статистическим данным:

    Уходят больше всего из отделов 'sales' и 'technology', на что следует обратить внимание.
    Самое же интересное, что уходят в основном младшие позиции с низкой и средней загрузкой, не получавшие повышений за год.
    Вероятно, причиной ухода в основном становится отсутствие возможностей карьерного роста ввиду нехватки задач.
    Зарплаты ушедших явно в среднем ниже, в купе с прошлым выводом это даёт нам портрет недостаточно загруженного задачами junior/middle сотрудника,
    который не видит в компании возможностей для карьерного роста, однако имеет амбиции такого рода.
   
7. Добавление признака job_satisfaction_rate (таргет, предсказанный в задаче 1)
8. Подготовка пайплайна предобработки и обучения
9. Поиск лучших моделей и гиперпараметров с помощью RandomizedSearchCV

### Итоговые выводы по задаче 2
Лучше всего себя показала модель DecisionTreeClassifier, гиперпараметры можно найти в тетрадке (вкладка 'Обучение моделей' в задаче 2), ROC-AUC ~=0.93.

## Итоговые выводы по проекту
1. **Портрет увольняющегося сотрудника**: Junior/Middle специалист, имеющий амбиции карьерного роста, однако не получающий достаточно нагрузки, и, как следствие, повышение.
2.  Статистика отделов по увольнениям

    доля увольнений от 348 сотрудников hr = 23.6%, всего уволилось 82
    
    доля увольнений от 423 сотрудников marketing = 26.5%, всего уволилось 112
    
    доля увольнений от 430 сотрудников purchasing = 27.9%, всего уволилось 120
    
    доля увольнений от 805 сотрудников sales = 23.7%, всего уволилось 191
    
    доля увольнений от 581 сотрудников technology = 25.8%, всего уволилось 150

3. Система оценки удовлетворённости работает: видна явная связь между уходом сотрудника из компании и низким индексом удовлетворённости.
