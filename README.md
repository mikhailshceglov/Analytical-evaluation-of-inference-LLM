# Ответы на ключевые вопросы

## Проблема

Инференс больших языковых моделей является трудоемкой задачей, а существующие аналитические оценки охватывают узкий круг параметров.

## Актуальность

Масштаб нагрузки значителен: согласно [отчёту OpenAI за 2025 год](https://openai.com/business/guides-and-resources/the-state-of-enterprise-ai-2025-report/),
более 9000 организаций обработали через API свыше 10 млрд токенов каждая, почти 200 - свыше 1 трлн.
По [оценке МЭА](https://www.iea.org/reports/energy-and-ai/energy-demand-from-ai), 
все центры обработки данных потребили около 415 ТВт/ч электроэнергии в 2024 году.
эта оценка относится ко всем ЦОД, а не только к инференсу LLM. Прогноз пропускной способности при заданной нагрузке
позволяет обоснованнее выбирать число GPU и предел параллелизма. Такой инструмент поможет сэкономить деньги на тестовых запусков,
сократить время потраченных человекочасов, увеличит скорость развертывания сервера.

## Объект исследования

Процесс параллельной обработки запросов к большой языковой модели на GPU.

## Предмет исследования

Пропускная способность процесса параллельной обработки запросов.

## Цель дипломного исследования

Разработать и проверить аналитическую модель зависимости RPS от числа одновременных запросов
для перечня маленьких LLM на 1 или 2 движках под конкретные GPU с учётом длительности шагов вычисления и ёмкости KV-кэша.

## Цель на текущий семестр

Изучить существующие методы, придумать математическую модель, собрать данные под разные конфигурации.

## Задачи

1. Сопоставить подходы к оценке производительности инференса в 
[Vidur](https://proceedings.mlsys.org/paper_files/paper/2024/hash/b74a8de47d2b3c928360e0a011f48351-Abstract-Conference.html)
и
[BLIS](https://arxiv.org/abs/2610.14255), выделить параметры, необходимые для собственной модели.
2. Сформулировать математическую модель зависимости RPS от числа одновременных запросов с учётом времени вычислительных шагов и ограничений KV-кэша.
3. Собрать и систематизировать измерения RPS и времени шагов для выбранных сочетаний LLM, движка, GPU и параметров нагрузки.

## Список использованных источников

1. OpenAI. *The State of Enterprise AI*. OpenAI, 2025. [URL](https://openai.com/business/guides-and-resources/the-state-of-enterprise-ai-2025-report/).
2. International Energy Agency. *Energy Demand from AI*. В отчёте *Energy and AI*, IEA, 2025. [URL](https://www.iea.org/reports/energy-and-ai/energy-demand-from-ai).
3. Agrawal A., Kedia N., Mohan J., Panwar A., Kwatra N., Gulavani B. S., Ramjee R., Tumanov A. *Vidur: A Large-Scale Simulation Framework for LLM Inference*. Proceedings of Machine Learning and Systems, 2024. [Статья](https://proceedings.mlsys.org/paper_files/paper/2024/hash/b74a8de47d2b3c928360e0a011f48351-Abstract-Conference.html).
4. Guhathakurta D., Toslali M., Parthasarathy S., Chen J., Kalantar M., Masluk N. A., Ramani V., Tantawi A., Oliveira F. *Simulate Before You Scale: High-Fidelity LLM Inference Planning Without GPUs* (BLIS). arXiv, 2026. [Статья](https://arxiv.org/abs/2610.14255).
