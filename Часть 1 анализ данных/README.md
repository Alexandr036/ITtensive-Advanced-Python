### 01 numpy и pandas Задание -  импорт данных
#### Задача
Возьмите данные по вызовам пожарных служб в Москве за 2015-2019 годы: https://video.ittensive.com/python-advanced/data-5283-2019-10-04.utf.csv
Получите из них фрейм данных (таблицу значений).
По этому фрейму вычислите среднее значение вызовов пожарных машин в месяц в одном округе Москвы, округлив до целых
_Примечание: найдите среднее значение вызовов, без учета года_

__Метод решения:__
1. Подключим библиотеку pandas.
2. Загрузим данные в дата фрейм при помощи read_csv. Выведем шапку дата фрейма, чтобы убедиться, что все корректно загрузилось.
3. Выведем среднее значение вызовов пожарных машин в месяц, в одном округе Москвы, округлив до целых.
___
 ### 02 Индексы и объединение фреймов - Задание - данные из нескольких источников
 #### Задача
Получите данные по безработице в Москве: https://video.ittensive.com/python-advanced/data-9753-2019-07-25.utf.csv
Объедините эти данные индексами (Месяц/Год) с данными из предыдущего задания (вызовы пожарных) для Центральный административный округ: https://video.ittensive.com/python-advanced/data-5283-2019-10-04.utf.csv
Найдите значение поля UnemployedMen в том месяце, когда было меньше всего вызовов в Центральном административном округе.

__Метод решения:__
1. Подключим библиотеку pandas.
2. Загрузим данные в дата фрейм при помощи read_csv. Выведем шапку дата фреймов, чтобы убедиться, что все корректно загрузилось.
3. Из первого и второго набора данных удалим не нужные колонки.
4. Переименуем колонки в наборах данных.
5. Создадим список номеров индекса центрального округа.
6. Создадим список значений округа по ранее созданному списку индексов центрального округа.
7. Добавим в наш дата фрейм еще одну серию и скажем, что это индекс наших зон.
8. После этого назначим мульти индекс.
9. Сделаем срез данных по значению мульти индекса "Центральный".
10. Объединим данные по индексам.
11. Найдем минимальное количество вызовов и выведем их.
___
### 03 Фильтрация и изменение данных- Задание - выделение данных
 #### Задача
Получите данные по безработице в Москве: https://video.ittensive.com/python-advanced/data-9753-2019-07-25.utf.csv
Найдите, с какого года процент людей с ограниченными возможностями (UnemployedDisabled) среди всех безработных (UnemployedTotal) стал меньше 2%.

__Метод решения:__
1. Подключим библиотеку pandas.
2. Загрузим данные в дата фрейм при помощи read_csv. Выведем шапку дата фрейма, чтобы убедиться, что все корректно загрузилось.
3.  Отфильтруем данные по условию, только те значения, когда процент людей с ограниченными возможностями (UnemployedDisabled) среди всех безработных (UnemployedTotal) стал меньше 2%.
4. Выведем первое значение года из набора данных через срез iloc[0:1], это и будет ответ на поставленную задачу.
_Также можно решить через lambda функцию, такой пример решения также приложен в файле_
___

### 04 Линейная регрессия - Задание - предсказание на 2020 год
 #### Задача
Возьмите данные по безработице в городе Москва: video.ittensive.com/python-advanced/data-9753-2019-07-25.utf.csv
Сгруппируйте данные по годам, и, если в году меньше 6 значений, отбросьте эти годы.
Постройте модель линейной регрессии по годам среднего значения отношения UnemployedDisabled к UnemployedTotal (процента людей с ограниченными возможностями) за месяц и ответьте, какое ожидается значение процента безработных инвалидов в 2020 году при сохранении текущей политики города Москвы?
Ответ округлите до сотых.

__Метод решения:__
1. Подключим библиотеку pandas, numpy и LinearRegression из библиотеки sklearn.linear_model.
2. Загрузим данные в дата фрейм при помощи read_csv. Выведем шапку дата фрейма, чтобы убедиться, что все корректно загрузилось.
3. Через лямбда функцию сформируем серию данных процент людей с ограниченными возможностями по отношению к общему числу безработных.
4. Отфильтруем данные, отбросив все значения не удовлетворяющие условию "если в году меньше 6 значений".
5. Получим новый фрейм данных data_avg сгруппировав данные во фрейме data по году, со средними значениями по проценту людей с ограниченными возможностями по отношению к общему числу безработных.
6.  Взьмем индекс данных (год) из data_avg преобразуем его к таблице по средствам 
reshape
7. Аналогично поступим серией данных значений по проценту людей с ограниченными возможностями по отношению к общему числу безработных в data_avg
8. Вызовем модель LinearRegression() и вгрузим в нее данные по средством fit(x, y)
9. Выведем предсказания по средством (model.predict(np.array(2020).reshape(1, 1))
___
