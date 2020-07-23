# Обзор некоторых моделей и подходов к решению задачи
## Нейросетевые подходы
### PlaneNet 
[Ссылка на статью](https://arxiv.org/pdf/1804.06278.pdf)

Особенности:
1. Первая end-to-end модель на нейронных сетях для сегментации плоскостей на изображении.
2. Возвращает карту глубины и ориентацию плоскостей.
3. Основное ограничения
    1. Максимальное кол-во плоскотей является гиперпараметром модели.
    2. Плохо справляется с шумными изображениями и с малыми поверхностями.
4. Обучение и тестирование проводилось на ScanNet и NYUv2 датасетах.
5. Реализованная авторами модель написана на втором питоне. [repo](https://github.com/art-programmer/PlaneNet)
6. Слабая обощающая способоность (согласно [данной статье](https://arxiv.org/pdf/1812.04072.pdf)).

### PlaneRCNN 
[Ссылка на статью](https://arxiv.org/pdf/1812.04072.pdf)

Особенности:
1. Убрано ограничение на количество распознаваемых плоскостей на изображении.
2. Основано на Mask R-CNN (вместо детектирования отдельных объектов настраивается на детектирование плоскость/не плоскость).
3. Добольно сложная и многоступенчатая архитектура сети. 
4. Есть репо от создателей на Python3, но с запуском пока не вышло. [repo](https://github.com/NVlabs/planercnn)
5. Достаточно интересные примеры есть работы с данными с улицы, а не внутреннего помещения.
6. Обучались все также на ScanNet и NYUv2.
7. Есть описание железа, которое использовалось при построении сети.

### Associative Embeddings 
[Ссылка на статью](https://arxiv.org/pdf/1902.09777.pdf)

Особенности:
1. На момент апреля 2019 года - SOTA решение в своей области.
2. Все те же датасеты (ScanNet - 256 x 192, NYUv2 - 640 x 480). Сразу вопрос: как это все будет работать с изображениями высокого разрешения.
3. Использована интересная идея: обучение эмбеддингов, которые отображают пиксели с одной плоскости в близкие точки (в один кластер).
4. Предложен оптимизированный алгоритм кластеризации эмбеддингов.
5. Есть упоминания методов построения обучающей выборки с помощью одной из модификаций RANSAC (до конца пока не разобрался с тем, как они это делали).
6. Нет ограничений на максимальное количество плоскотей, содержащихся на изображении. (!!!)
7. Возможно применение в реалтайме (по данным из статьи видно, что модель работает со скоростью 32 FPS). Интересно проверить скорость на изображения с большим разрешением.
8. Возвращает карту глубины и ориентацию плоскостей. 
9. Описаны технические мощности, на которых авторы проверяли свои наработки.
10. Есть авторская реализация на Python3. [repo](https://github.com/svip-lab/PlanarReconstruction)



