# Анализатор данных

Этот проект был разработан для хакатона и представляет собой инструмент для анализа данных с использованием методов машинного обучения. Проект состоит из двух частей: фронтенда и бэкенда.

## Show case

https://drive.google.com/drive/folders/1iAEv-dDhbJUiIz2zLObA2mNiagUzrvdE?usp=drive_link

## Установка и запуск

### С использованием Docker

1. Убедитесь, что у вас установлен Docker и Docker Compose.
2. В корневой директории проекта выполните команду:

    ```sh
    docker-compose up --build
    ```

### Локально

1. Установите зависимости для фронтенда:

    ```sh
    cd analizer_frontend
    npm install
    ```

2. Установите зависимости для бэкенда:

    ```sh
    cd ../analizer_backend
    pip install -r requirements.txt
    ```

3. Запустите фронтенд и бэкенд:

    ```sh
    cd ..
    ./start.sh
    ```

## Использование

1. Перейдите на [http://localhost:3000](http://localhost:3000) для доступа к фронтенду.
2. Загрузите файл в формате CSV или Excel на главной странице.
3. Перейдите к статистическому анализу данных.
4. Выберите колонки для анализа и тип графика.
5. Перейдите к анализу данных методами машинного обучения.

## Команды

- `npm start` - Запуск фронтенда в режиме разработки.
- `npm run build` - Сборка фронтенда для продакшена.
- `python3 main.py` - Запуск бэкенда.

## Препроцессинг текстовых данных
### 1. Проверка входных данных:
Если текст пустой или содержит значение NaN, возвращается пустая строка.
Очистка текста:
### 2. Перевод в нижний регистр.
Замена сокращений с помощью метода expand_abbreviations.
Удаление URL, адресов электронной почты.
### 3. Обработка эмодзи:
Замена эмодзи их текстовыми описаниями (например, 😊 → ':smile:') с помощью библиотеки emoji.
### 4. Удаление специальных символов:
Убираются все символы, кроме букв, цифр, пробелов и дефисов (например, @#$ → пробел).
Избыточные пробелы заменяются одиночным пробелом.
### 5. Токенизация и лемматизация:
Разбивает текст на слова.
Для каждого слова:
Проверяет, что длина больше двух символов и слово не является стоп-словом.
Определяет начальную форму слова (лемму) с помощью pymorphy2.
Исключает слова с частями речи, которые не важны для анализа (предлоги, союзы, частицы, междометия).
### 6. Собирает обработанные слова обратно в строку.

## Кластеризация данных
### Основные возможности
1. Обработка числовых данных:
Масштабирование данных с использованием стандартизации (StandardScaler).
Вычисление глобальных статистик (среднее, медиана, стандартное отклонение, квартильные значения) для глубокого анализа данных.
2. Обработка текстовых данных:
Преобразование текстов в числовые векторы с использованием мультиязычной модели BERT (Symanto SN-XLM-RoBERTa).
Выделение ключевых слов из текстов с помощью TF-IDF и анализа наиболее центральных документов.
3. Кластеризация:
Использование HDBSCAN для формирования кластеров с учетом гибкости в размере кластеров и устойчивости к шуму.
Поддержка эвклидовой метрики для работы с комбинированными пространствами признаков.
4. Автоматизация анализа:
Генерация текстовых описаний кластеров на основе статистики числовых признаков и выделенных ключевых слов.
Обнаружение аномалий и их выделение в отдельные шумовые группы.
5. Визуализация кластеров:
Использование UMAP для уменьшения размерности данных и наглядного представления кластеров на графиках.
### Ключевые особенности
1. Интеграция числовых и текстовых данных: Класс объединяет гетерогенные типы данных, позволяя эффективно работать с реальными бизнес-кейсами.
2. Гибкость модели: Настраиваемые параметры минимального размера кластеров, метрик и алгоритмов снижения размерности.
3. Умный анализ: Автоматическое выделение ключевых особенностей кластеров и формирование интерпретируемых описаний для каждого сегмента.
   
## Авторы

- Сафронов Илья (бэкенд/фронтенд)
- Блувштейн Елизавета (ml)
- Кулаков Дмитрий (ml)
