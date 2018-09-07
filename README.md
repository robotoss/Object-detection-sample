<div align="center">
  <a href="https://nanonets.com/objectdetection/">
    <img src="https://nanonets.com/logo.png" alt="NanoNets Object Detection Python Sample" width="100"/>
    </a>
</div>

<h1 align="center">NanoNets Object Detection Python Sample</h1>

| [Golang Sample](https://github.com/NanoNets/object-detection-sample-golang) | [Python Sample](https://github.com/NanoNets/object-detection-sample-python)| [Node.js Sample](https://github.com/NanoNets/object-detection-sample-nodejs) |  [PHP Sample](https://github.com/NanoNets/object-detection-sample-php) |
| -------------------------- |--------------------------|--------------------------| --------------------------|
| [![](https://www.hugopicado.com/assets/golang.png)](https://github.com/NanoNets/object-detection-sample-golang) | [![](http://kata.coderdojo.com/images/thumb/e/ea/Python_logo.png/100px-Python_logo.png)](https://github.com/NanoNets/object-detection-sample-python) | [![](https://s3.amazonaws.com/openshift-hub/production/quickstarts/243/nodejs_custom.png?1456926624)](https://github.com/NanoNets/object-detection-sample-nodejs) | [![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/100px-PHP-logo.svg.png)](https://github.com/NanoNets/object-detection-sample-php) | 

** **

## Распознавание Тысячелетнего Сокола

Картинки и аннотации были взяты из Images and annotations taken from - https://github.com/bourdakos1/Custom-Object-Detection

Изображение состоит из кадров взятых из клипа Звездные Войны - Пробуждение Силы
[![Watch the video](https://github.com/bourdakos1/Custom-Object-Detection/raw/master/screenshots/starwars_small.gif)](https://www.youtube.com/watch?v=xW2hpkoaIiM)

Аннотации присутствуют для каждого кадра и имеют то же имя, что и имя изображения. Вы можите найти пример для обучения модели в Python и Node, обновив API-ключ и модель ID в соотвествующим файле. Там так же присутсвует папка с предварительно обработаными аннотации json которые готовы к загрузке для Nanonets API.



** **

# Создание Детектора Объектов для Тысячелетнего Сокола

>**Заметка:** Убедитесь что у Вас в системе установлен python и pip, если у Вас еще они не установлены посетите
[Python](https://www.python.org/downloads/release/python-2714/)
[pip](https://pip.pypa.io/en/stable/installing/)
 
### Шаг 1: Скопируйте репозиторий, установите зависимости
```bash
git clone https://github.com/NanoNets/object-detection-sample-python.git
cd object-detection-sample-python
sudo pip install requests tqdm
```

### Шаг 2: Получите свой бесплатный API ключ
Получите свой бесплатный API ключ на http://app.nanonets.com/user/api_key

### Шаг 3: Установите API ключ в еременную Середу
```bash
export NANONETS_API_KEY=YOUR_API_KEY_GOES_HERE
```

### Шаг 4: Создание новой модели
```bash
python ./code/create-model.py
```
 >_**Заметка:** Данная опреация создаст MODEL_ID который потребуется Вам в следующем шаге

### Шаг 5: Добавте ID Модель в Переменную Середу
```bash
export NANONETS_MODEL_ID=YOUR_MODEL_ID
```
 >_**Заметка:** вы получите YOUR_MODEL_ID из предыдущего шага

### Шаг 6: Загрузка Обучающих Материалов
Обучающие материалы находяться в ```images``` (файлы изображения) и ```annotations``` (аннотация для файлов изображения)
```bash
python ./code/upload-training.py
```

### Шаг 7: Обучение Модели
Как только изображения будут загружены, начните обучение модели
```bash
python ./code/train-model.py
```

### Шаг 8: Получение состояние модели
Обучение модель займет около 2х часов. Когда обучение будет закончено, вы получете email оповещение. Проверте состояние модели
```bash
python ./code/model-state.py
```

### Шаг 9: Запуск Прогноза
Когда модель будет обучена запустить прогназирования используя модель.
```bash
python ./code/prediction.py PATH_TO_YOUR_IMAGE.jpg
```

**Пример использования:**
```bash
python ./code/prediction.py ./images/videoplayback0051.jpg
```


*Обратите внимание, что образец python использует преобразованный json вместо полезной нагрузки xml для удобства, следовательно, он не имеет зависимостей.*
