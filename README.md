# llm-resource-allocation
resource allocation between agents in a multi-agent system based on large language models


## Цель проекта: Разработка мультиагентной системы с теоретико-игровым распределением LLM-ресурсов для решения сложных задач из бенчмарка GAIA.

### Основные компоненты:

* Декомпозитор → разбивает задачи GAIA на последовательные подзадачи
* Оракул → генерирует "кубик оценок" (тензор U[M×N×K])
* Роутер → распределяет подзадачи по агентам с использованием критериев справедливости (NSW, EF, USW)
* Агенты (3 типа: RESEARCHER, ANALYST, PROGRAMMER) → исполняют подзадачи

<img width="491" height="201" alt="image" src="https://github.com/user-attachments/assets/c91600e0-fd36-4ed7-a535-f85a01536ab2" />


### Техническая реализация:

Используется OpenRouter API с тремя моделями: GPT-4o-mini, Claude-3 Haiku, Llama-3 8B

Бюджет ограничен, поэтому нужна экономия токенов

Оракул использует гибридный подход (эвристика + выборочные LLM-запросы)

### Научная новизна:

Применение теории игр к распределению LLM-ресурсов

Концепция "кубика оценок" для многомерной оценки совместимости

Использование fairness критериев (Nash Social Welfare, Envy-Freeness)

### Текущий статус:

Реализована архитектура системы

Настроена интеграция с OpenRouter

Создан OptimizedOracle с матрицами совместимости
Проведен анализ стабильности генерации оценок
<img width="4170" height="2966" alt="stability_analysis" src="https://github.com/user-attachments/assets/6653a2fa-b466-41f1-9fd7-90c3492815cb" />


Проведены первые тесты API

Создано три типа роутинга (USW, NSW и просто равномерное распределение)
<img width="1389" height="990" alt="Compare_p" src="https://github.com/user-attachments/assets/1ed54ffc-ab26-48dd-bf9c-353a0fb3989e" />

