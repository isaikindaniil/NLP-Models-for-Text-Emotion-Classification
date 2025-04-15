# NLP-Models-for-Text-Emotion-Classification

Всем привет 👋 

Данный репозиторий представляет собой NLP модели, которые помогают классифицировать настроение в тексте. Они могут быть полезны для анализа отзывов и обратной связи клиентов, маркетинга и коммуникации, а также модерации контента.

## О проекте

За основу был взят открытый датасет с сайта kaggle (https://www.kaggle.com/datasets/simaanjali/emotion-analysis-based-on-text), он состоит из более чем 800 тысяч строк, в которых есть признаки данных эмоций: 
- нейтральный текст (neutral)
- выражения любви (love)
- печаль (sadness)
- чувство облегчения (relief)
- ненависть (hate)
- злость (anger)
- веселье/радость (fun)
- энтузиазм (enthusiasm)
- удивление (surprise)
- пустота (empty)
- беспокойство (worry)
- скука (boredom)

## Реализованные модели

В проекте реализованы две модели:

1. **emotion_classification_model** - NLP модель классификации на основе TF-IDF векторизации текста с классическим алгоритмом логистической регрессии.
   - Точность на тестовых данных: ~99%
   - Быстрая работа на CPU
   - Компактный размер модели

2. **bert_emotion_model** - NLP модель классификации на основе готовой BERT модели, дообученной (fine-tuning) для классификации настроений в текстах.
   - Точность на тестовых данных: ~98%
   - Более глубокое понимание контекста текста
   - Требует больше вычислительных ресурсов, но работает эффективнее с новыми данными

## Структура репозитория

- `emotion_class_models.ipynb` - Jupyter notebook с полным процессом обучения моделей и предобработки данных
- `example.ipynb` - Пример использования готовых моделей для классификации текстов
- `emotion_classification_model.pkl` - Сохраненная TF-IDF + LogReg модель
- `bert_emotion_model/` - Директория с сохраненной BERT моделью
- `README.md` - Документация проекта

## О ноутбуке emotion_class_models.ipynb

Основной ноутбук содержит весь процесс создания моделей классификации эмоций и включает следующие этапы:

1. **Загрузка и исследование данных**:
   - Загрузка датасета с около 840,000 записей
   - Анализ распределения эмоций (наиболее часто встречается "neutral" - 674,538 примеров)
   - Визуализация данных с помощью seaborn и matplotlib

2. **Предобработка текста**:
   - Приведение текста к нижнему регистру
   - Удаление URL-адресов, специальных символов, цифр
   - Удаление стоп-слов (частых слов, не несущих смысловой нагрузки)
   - Лемматизация (приведение слов к базовой форме)

3. **Анализ токенов**:
   - Извлечение наиболее часто встречающихся слов для каждой эмоции
   - Например, для эмоции "hate" наиболее частыми словами оказались "feel", "hate", "feeling", "hated"

4. **Разработка моделей**:
   - TF-IDF векторизация текста и обучение логистической регрессии
   - Fine-tuning BERT модели на данном наборе данных
   - Оценка и сравнение моделей с использованием метрик точности, F1-score и визуализации матрицы ошибок

5. **Тестирование и валидация**:
   - Проверка моделей на отдельных примерах
   - Интерактивный интерфейс для тестирования классификации

## Использование

Вы можете самостоятельно изучить процесс написания каждой из модели, а также предобработки данных в рамках тетрадки (`emotion_class_models.ipynb`). Код написан таким образом, чтобы легко можно было внести изменения и воспользоваться им для создания (а также модификации и улучшения работоспособности) новых моделей классификации на других датасетах, к примеру для создания классификатора токсичности текстов.

В тетрадке `example.ipynb` вы можете ознакомиться с примером использования готовых моделей для собственных целей, а также протестировать их на сторонних текстах.


## Технические требования

Для работы с проектом вам потребуется:

- Python 3.8+
- pandas
- numpy
- scikit-learn
- torch
- transformers
- nltk
- joblib
- matplotlib
- seaborn

### Установка зависимостей

`pip install -r requirements.txt`

### Содержимое requirements.txt

`pandas==2.0.0
numpy==1.24.3
scikit-learn==1.2.2
torch==2.0.0
transformers==4.28.1
nltk==3.8.1
joblib==1.2.0
matplotlib==3.7.1
seaborn==0.12.2`


## Вклад в проект

Буду рад любому, кто желает внести вклад в развитие данного репозитория, а также обратной связи по использованию данных моделей.

Вы можете:
- Добавить поддержку новых языков
- Улучшить предобработку текста
- Реализовать дополнительные модели
- Добавить веб-интерфейс для демонстрации возможностей

## Лицензия

[MIT License](LICENSE)

-----------------------------------------------------------------
Hello 👋 

This repository contains NLP models that help classify emotions in text. They can be useful for analyzing customer reviews and feedback, marketing and communication, and content moderation.

## About the Project

The models were built using an open dataset from Kaggle (https://www.kaggle.com/datasets/simaanjali/emotion-analysis-based-on-text), which consists of more than 800,000 lines with the following emotion labels: 
- neutral
- love
- sadness
- relief
- hate
- anger
- fun
- enthusiasm
- surprise
- empty
- worry
- boredom

## Implemented Models

Two models have been implemented:

1. **emotion_classification_model** - NLP classification model based on TF-IDF text vectorization with a classic logistic regression algorithm.
   - Test accuracy: ~99%
   - Fast performance on CPU
   - Compact model size

2. **bert_emotion_model** - NLP classification model based on a pre-trained BERT model fine-tuned for emotion classification in texts.
   - Test accuracy: ~98%
   - Deeper understanding of text context
   - Requires more computational resources but works more effectively with new data

## Repository Structure

- `emotion_class_models.ipynb` - Jupyter notebook with the full process of training models and data preprocessing
- `example.ipynb` - Example of using ready-made models for text classification
- `emotion_classification_model.pkl` - Saved TF-IDF + LogReg model
- `bert_emotion_model/` - Directory with the saved BERT model
- `README.md` - Project documentation

## About the emotion_class_models.ipynb Notebook

The main notebook contains the entire process of creating emotion classification models and includes the following stages:

1. **Data Loading and Exploration**:
   - Loading the dataset with approximately 840,000 records
   - Analysis of emotion distribution (most frequent is "neutral" - 674,538 examples)
   - Data visualization using seaborn and matplotlib

2. **Text Preprocessing**:
   - Converting text to lowercase
   - Removing URLs, special characters, and digits
   - Removing stop words (frequent words that don't carry meaning)
   - Lemmatization (reducing words to their base form)

3. **Token Analysis**:
   - Extracting the most frequently occurring words for each emotion
   - For example, for the emotion "hate" the most common words were "feel", "hate", "feeling", "hated"

4. **Model Development**:
   - TF-IDF text vectorization and training logistic regression
   - Fine-tuning BERT model on this dataset
   - Evaluation and comparison of models using accuracy metrics, F1-score, and confusion matrix visualization

5. **Testing and Validation**:
   - Testing models on individual examples
   - Interactive interface for classification testing

## Usage

You can independently study the process of creating each model, as well as data preprocessing, in the notebook (`emotion_class_models.ipynb`). The code is written in a way that makes it easy to make changes and use it to create (as well as modify and improve the performance of) new classification models on other datasets, for example, to create a text toxicity classifier.

In the notebook `example.ipynb`, you can see examples of using the ready-made models for your own purposes, and test them on external texts.


## Technical Requirements

To work with this project you will need:

- Python 3.8+
- pandas
- numpy
- scikit-learn
- torch
- transformers
- nltk
- joblib
- matplotlib
- seaborn

### Installing Dependencies

`pip install -r requirements.txt`


### Contents of requirements.txt

`pandas==2.0.0
numpy==1.24.3
scikit-learn==1.2.2
torch==2.0.0
transformers==4.28.1
nltk==3.8.1
joblib==1.2.0
matplotlib==3.7.1
seaborn==0.12.2`


## Contributing to the Project

I welcome anyone who wishes to contribute to the development of this repository, as well as any feedback on using these models.

You can:
- Add support for new languages
- Improve text preprocessing
- Implement additional models
- Add a web interface to demonstrate capabilities

## License

[MIT License](LICENSE)

