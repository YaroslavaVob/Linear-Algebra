## <center> Линейная алгебра в контексте линейных методов. </center>

**На основе небольшого датасета о добыче газа на скважинах мы построим линейную регрессию с помощью метода наименьших квадратов.**

### <center>**Цель проекта**</center>
**Построить различные регрессионные модели ML, провести сравнительный анализ моделей и выбрать наилучшую для решения задачи прогноза выработки газа на основе характеристик скважины.**

<u>Таким образом, нам необходимо решить несколько основных задач:</u>
* провести разведывательный анализ данных и определить наиболее значимые для моделирования факторы, от которых зависит добыча газа - наша целевая переменная, которую мы должны спрогнозировать с минимальной ошибкой;
* построить простейшую линейную регрессию по методу наименьших квадратов;
* построить полиномиальные регрессии с различными способами регуляризации;
* определить наилучшую модель из сравнительного анализа качества созданных моделей.


#### **Данные, которые предоставил нам заказчик:**

* Well — идентификатор скважины;
* Por — пористость скважины (%);
* Perm — проницаемость скважины;
* AI — акустический импеданс ($кг/м^2 * 10^6$);
* Brittle — коэффициент хрупкости скважины (%);
* TOC — общий органический углерод (%);
* VR — коэффициент отражения витринита (%);
* ***Prod*** — добыча газа в сутки (млн. кубических футов) - ***целевая переменная***.
 
Все данные оказались числовыми, без пропусков и выбросов. Поэтому этап подготовки - очистки данных нам не понадобился.

### <center>**Этапы проекта**</center>
#### **Этап 1. Описательный, разведывательный анализы и построение простой линейной регрессии с помощью инструментов линейной алгебры из библиотеки numpy.**
1. Описательный и разведывательный анализ, включающий визуализацию признаков, а именно распределение каждого признака и зависимость от целевого.
Мы помним, что наш датасет очень небольшой и наша цель в данном проекте - это рассмотрение способов построения линейных регрессий. 
2. Одним из важных условий для решения уравнения линейной регрессии является сама матрица наших данных и главная ее характеристика - вырожденность. Поэтому мы проведем анализ матрицы корреляций.
3. Решение уравнения линейной регрессии и изучение полученных неизвестных коэффициентов уравнения.
4. Анализ коэффициентов корреляций и коэффициентов регрессии помогут нам определить значимости факторов и исключить те из них, которые обладают коллинарностью/мультиколлинеарностью и искажают прогностическую способность модели, делают ее неустойчивой.

#### **Этап 2. Создание линейных регрессий на полиномиальных признаках и с использованием различных методов регуляризации.**
1. Внедрение полинома 3-й степени для решения уравнения регрессии. Для обеспечения сходимости мы прежде стандартизируем наши признаки с помощью StandardScaler, так как наши данные более-менее нормального распределения.
2. Полиномиальная регрессия с $L_1$-регуляризацией.
3. Полиномиальная регрессия с $L_2$-регуляризацией.
4. Полиномиальная регрессия с $L_1$ и $L_2$-регуляризациями (ElasticNet).

#### **Этап 3. Сравнительный анализ значений метрик всех моделей и подведение итогов.**
- Мы математическим способом показали, как находить плохо обусловленные данные, а именно с помощью построения матрицы корреляций, изучения ранга и определителя матрицы. При "плохих" данных мы можем получить непредсказуемые результаты, которые вообще не будут обладать хоть какой-то предсказательной способностью, поэтому важно изучать коэффициенты регрессии и выявлять "сбои" прежде, чем строить модель ML. А такие факторы необходимо исключить из данных для моделирования.
- Мы представили все варианты регрессий с различными уравнениями и для нашей задачи оптимальной оказалась полиномиальная регрессия с $L_1$-регуляризацией(Lasso), которая накладывает штраф на сумму модулей весов и "обнуляет" высококоллинеарные признаки, тем самым сохраняя линейную независимость между факторами.

<font color='orange'>ПРИМЕЧАНИЕ</font> После каждого этапа проекта имеются подробные выводы. 

А теперь переходим по ссылке и знакомимся с проектом [здесь](https://github.com/YaroslavaVob/Linear-Algebra/blob/main/MATH_ML-2.%D0%9F%D1%80%D0%B0%D0%BA%D1%82%D0%B8%D0%BA%D0%B0.LinearRegression.ipynb).


### Какие библиотеки использовались для анализа:
<font color = 'springblue'>pandas</font>\
<font color = 'springblue'>numpy</font>\
<font color = 'springblue'>sklearn</font>\
<font color = 'springblue'>matplotlib</font>\
<font color = 'springblue'>seaborn</font>




**Проект создан на базе языка Python в Jupyter Notebook.**

Автор: Ярослава Вобшаркян\
(студент школы SkillFactory по курсу Data Science)
