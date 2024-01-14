# Домашнее задание к занятию «Микросервисы: подходы»
- Вы работаете в крупной компании, которая строит систему на основе микросервисной архитектуры. Вам как DevOps-специалисту необходимо выдвинуть предложение по организации инфраструктуры для разработки и эксплуатации.
### Задача 1: Обеспечить разработку
- Предложите решение для обеспечения процесса разработки: хранение исходного кода, непрерывная интеграция и непрерывная поставка. Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.
- Решение должно соответствовать следующим требованиям:
  - облачная система;
  - система контроля версий Git;
  - репозиторий на каждый сервис;
  - запуск сборки по событию из системы контроля версий;
  - запуск сборки по кнопке с указанием параметров;
  - возможность привязать настройки к каждой сборке;
  - возможность создания шаблонов для различных конфигураций сборок;
  - возможность безопасного хранения секретных данных (пароли, ключи доступа);
  - несколько конфигураций для сборки из одного репозитория;
  - кастомные шаги при сборке;
  - собственные докер-образы для сборки проектов;
  - возможность развернуть агентов сборки на собственных серверах;
  - возможность параллельного запуска нескольких сборок;
  - возможность параллельного запуска тестов.
- Обоснуйте свой выбор.
### Ответ: Решение для обеспечения процесса разработки, удовлетворяющее указанным требованиям, может включать в себя следующие программные продукты:
- GitLab CI/CD:
Облачная система: GitLab предоставляет возможность использования как облачной версии, так и развертывания на собственном сервере.
Система контроля версий Git: GitLab интегрирован с Git и предоставляет встроенные средства для управления репозиториями Git.
Репозиторий на каждый сервис: GitLab позволяет создавать репозитории для каждого сервиса, обеспечивая изолированное хранение кода.
Запуск сборки по событию из системы контроля версий: GitLab CI/CD может автоматически запускать сборку при изменениях в репозитории.
- Docker:
Собственные докер-образы для сборки проектов: Использование Docker обеспечивает стандартизированное окружение для сборки и развертывания приложений.
- HashiCorp Vault:
Безопасное хранение секретных данных: Vault предоставляет безопасное хранение и управление секретами, что позволяет сохранять и использовать пароли, ключи доступа и другие секреты.
- Jenkins:
Запуск сборки по кнопке с указанием параметров: Jenkins предоставляет гибкую настройку сборок, включая возможность ручного запуска с указанием параметров.
Возможность привязать настройки к каждой сборке: Jenkins позволяет настраивать конфигурации сборок, привязывая настройки к каждой из них.
- Jenkins Templating Engine (JTE) или Jenkins Job DSL:
Возможность создания шаблонов для различных конфигураций сборок: Использование JTE или Job DSL позволяет создавать шаблоны для унификации и автоматизации конфигураций сборок.
- Jenkins Agent:
Возможность развернуть агентов сборки на собственных серверах: Jenkins поддерживает децентрализованную сборку, позволяя развертывать агентов сборки на различных серверах.
- Parallel Stages в Jenkins:
Возможность параллельного запуска нескольких сборок и тестов: Использование Parallel Stages в Jenkins позволяет параллельно выполнять различные этапы сборки и тестирования.
Такой набор инструментов обеспечивает полноценный цикл разработки, интеграции и поставки приложений, обеспечивая высокую степень гибкости, безопасности, и управления.
### Задача 2: Логи
- Предложите решение для обеспечения сбора и анализа логов сервисов в микросервисной архитектуре. Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.
- Решение должно соответствовать следующим требованиям:
  - сбор логов в центральное хранилище со всех хостов, обслуживающих систему;
  - минимальные требования к приложениям, сбор логов из stdout;
  - гарантированная доставка логов до центрального хранилища;
  - обеспечение поиска и фильтрации по записям логов;
  - обеспечение пользовательского интерфейса с возможностью предоставления доступа разработчикам для поиска по записям логов;
  - возможность дать ссылку на сохранённый поиск по записям логов.
- Обоснуйте свой выбор.
### Ответ: Решение для сбора и анализа логов в микросервисной архитектуре:
- ELK стек (Elasticsearch, Logstash, Kibana):
  - Сбор логов в центральное хранилище: Logstash: Используется для сбора и обработки логов со всех хостов. Logstash может получать данные из различных источников, включая stdout.
- Минимальные требования к приложениям:
  - stdout: Логи должны быть направлены в stdout приложений, что является стандартной практикой для микросервисов.
- Гарантированная доставка логов:
  - Filebeat: Этот легкий агент обеспечивает надежную и эффективную доставку логов до Logstash.
- Обеспечение поиска и фильтрации:
  - Elasticsearch: Используется для хранения и индексации логов, что обеспечивает высокую производительность поиска и фильтрации.
- Пользовательский интерфейс для разработчиков:
  - Kibana: Предоставляет мощный веб-интерфейс для визуализации и анализа логов. Разработчики могут легко создавать запросы и фильтры, а также изучать данные в реальном времени.
- Ссылки на сохранённые поиски:
  - Kibana: Разработчики могут сохранять свои запросы и фильтры в Kibana, создавая постоянные ссылки на сохраненные поиски для будущего доступа.
- Обоснование выбора:
  - Гибкость и Масштабируемость:
  - ELK стек легко масштабируется, что особенно важно в микросервисной архитектуре, где количество логов может быть значительным. Elasticsearch обеспечивает горизонтальное масштабирование для управления растущим объемом данных.
  - Совместимость с различными источниками данных: Logstash поддерживает различные источники данных, что позволяет легко интегрировать его с разными компонентами микросервисной системы.
  - Богатые возможности визуализации: Kibana предоставляет мощные средства для визуализации и анализа данных, что делает его отличным инструментом для разработчиков, исследующих логи.
  - Открытый источник: ELK стек является открытым источником, что обеспечивает гибкость и возможность настройки под конкретные потребности компании без дополнительных расходов на лицензии.
  - Широкое применение в индустрии: ELK стек широко используется в индустрии и имеет активное сообщество, что обеспечивает поддержку и обновления.
  - Интеграция с Filebeat: Использование Filebeat для надежной доставки логов позволяет эффективно управлять процессом сбора данных с различных источников.
ELK стек является мощным и проверенным решением для сбора и анализа логов в микросервисной архитектуре, предоставляя все необходимые возможности, описанные в поставленных требованиях.
### Задача 3: Мониторинг
- Предложите решение для обеспечения сбора и анализа состояния хостов и сервисов в микросервисной архитектуре. Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.
- Решение должно соответствовать следующим требованиям:
  -сбор метрик со всех хостов, обслуживающих систему;
  -сбор метрик состояния ресурсов хостов: CPU, RAM, HDD, Network;
  -сбор метрик потребляемых ресурсов для каждого сервиса: CPU, RAM, HDD, Network;
  -сбор метрик, специфичных для каждого сервиса;
  -пользовательский интерфейс с возможностью делать запросы и агрегировать информацию;
  -пользовательский интерфейс с возможностью настраивать различные панели для отслеживания состояния системы.
-Обоснуйте свой выбор.
### Ответ: Решение для сбора и анализа состояния хостов и сервисов в микросервисной архитектуре:
- Prometheus и Grafana:
  - Сбор метрик со всех хостов:
  - Prometheus: Является системой мониторинга с открытым исходным кодом, спроектированной для сбора метрик из различных источников, включая хосты.
  - Сбор метрик состояния ресурсов хостов: Node Exporter: Экспортер Prometheus, который собирает метрики о состоянии хостов, включая CPU, RAM, HDD и сеть.
  - Сбор метрик потребляемых ресурсов для каждого сервиса: Prometheus (метрики HTTP/REST): Сервисы предоставляют метрики о своем состоянии, такие как использование CPU, RAM, сетевой трафик и другие через HTTP/REST API.
  - Сбор метрик, специфичных для каждого сервиса: Instrumentation в коде сервисов: Добавление кода (инструментирование) в каждый сервис для сбора специфичных метрик и экспорта их в Prometheus.
  - Пользовательский интерфейс для запросов и агрегации: Grafana: Интегрируется с Prometheus и предоставляет гибкий пользовательский интерфейс для создания запросов и визуализации метрик. Разработчики могут создавать сложные запросы для анализа состояния системы.
  - Настройка различных панелей: Grafana: Позволяет настраивать различные панели для отслеживания состояния системы. Разработчики могут создавать собственные дашборды, объединяя метрики различных сервисов.
- Обоснование выбора:
  - Простота и гибкость: Prometheus прост в установке и конфигурации, позволяя собирать метрики с различных источников. Гибкость в определении запросов и агрегаций делает его подходящим для микросервисной архитектуры.
  - Эффективность сбора метрик: Node Exporter обеспечивает эффективный сбор метрик о состоянии хостов без значительной нагрузки.
  - Интеграция с кодом сервисов: Добавление инструментации в код сервисов позволяет собирать метрики, специфичные для каждого сервиса, что важно для анализа производительности и выявления проблем.
  - Богатые возможности визуализации: Grafana предоставляет разработчикам возможность создавать красочные и информативные дашборды, что облегчает мониторинг и анализ состояния системы.
  - Открытый источник: Prometheus и Grafana являются проектами с открытым исходным кодом, что позволяет использовать их без лицензионных ограничений.
  - Активное сообщество и экосистема: Оба продукта имеют активные сообщества пользователей и широкую экосистему дополнений, что обеспечивает поддержку и расширяемость.
Использование Prometheus и Grafana обеспечит полноценный мониторинг состояния хостов и сервисов в микросервисной архитектуре, удовлетворяя поставленным требованиям.
