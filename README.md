# **Домашнее задание к занятию «Микросервисы: масштабирование»**-***Вуколов Евгений***
 
Вы работаете в крупной компании, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps-специалисту необходимо выдвинуть предложение по организации инфраструктуры для разработки и эксплуатации.
 
## Задача 1: Кластеризация
 
Предложите решение для обеспечения развёртывания, запуска и управления приложениями.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.
 
Решение должно соответствовать следующим требованиям:
- поддержка контейнеров;
- обеспечивать обнаружение сервисов и маршрутизацию запросов;
- обеспечивать возможность горизонтального масштабирования;
- обеспечивать возможность автоматического масштабирования;
- обеспечивать явное разделение ресурсов, доступных извне и внутри системы;
- обеспечивать возможность конфигурировать приложения с помощью переменных среды, в том числе с возможностью безопасного хранения чувствительных данных таких как пароли, ключи доступа, ключи шифрования и т. п.
 
Обоснуйте свой выбор.
 
## Задача 2: Распределённый кеш * (необязательная)
 
Разработчикам вашей компании понадобился распределённый кеш для организации хранения временной информации по сессиям пользователей.
Вам необходимо построить Redis Cluster, состоящий из трёх шард с тремя репликами.
 
### Схема:
 
![11-04-01](https://user-images.githubusercontent.com/1122523/114282923-9b16f900-9a4f-11eb-80aa-61ed09725760.png)
 
---
 
### Как оформить ДЗ?
 
Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.


# **Решение**

## Задача 1: Кластеризация

Для организации инфраструктуры микросервисной системы, соответствующей заданным требованиям, предлагается решение на основе Kubernetes в сочетании с дополнительными 
инструментами для обеспечения обнаружения сервисов, маршрутизации запросов и безопасного хранения конфигураций.

Решение
1. Kubernetes
- Поддержка контейнеров: Kubernetes является одним из лучших инструментов для оркестрации контейнеров, что позволяет эффективно управлять и развертывать приложения 
в контейнерах Docker или других форматах.

- Обнаружение сервисов и маршрутизация запросов: Kubernetes обеспечивает автоматическое обнаружение сервисов через DNS и механизмы балансировки нагрузки, 
что упрощает маршрутизацию запросов между микросервисами.

- Горизонтальное масштабирование и автоматическое масштабирование: Kubernetes поддерживает горизонтальное масштабирование приложений и автоматическое масштабирование на основе метрик, 
таких как CPU-утилизация.

Разделение ресурсов: Kubernetes позволяет использовать Namespaces для явного разделения ресурсов и доступа к ним, что обеспечивает изоляцию между разными частями системы.

2. Service Discovery
Обнаружение сервисов: Для более гибкого и динамического обнаружения сервисов можно использовать инструменты типа Consul или etcd. 
Эти инструменты позволяют микросервисам регистрироваться и обнаруживать друг друга в динамической среде.

3. Service Mesh (например, Istio)
Маршрутизация запросов и управление трафиком: Service Mesh, такой как Istio, обеспечивает более сложную маршрутизацию запросов, управление трафиком и мониторинг между микросервисами. 
Это позволяет реализовать более сложные сценарии, такие как A/B-тестирование или канареечные развертывания.

4. Конфигурирование приложений и безопасное хранение данных
Конфигурирование с помощью переменных среды: Kubernetes позволяет конфигурировать приложения с помощью ConfigMaps и Secrets, которые позволяют хранить конфигурационные данные и 
чувствительные информацию, такие как пароли или ключи доступа, в безопасном виде.

Безопасное хранение данных: Для безопасного хранения конфиденциальных данных можно использовать HashiCorp's Vault, который обеспечивает централизованное управление 
секретами и позволяет безопасно хранить и распространять конфиденциальную информацию между приложениями.

Обоснование выбора:

- Масштабируемость и гибкость: Kubernetes обеспечивает гибкое масштабирование и автоматическое масштабирование, что позволяет эффективно управлять ресурсами в зависимости от нагрузки.

- Обнаружение и маршрутизация сервисов: Использование Service Discovery и Service Mesh (например, Istio) позволяет реализовать динамическое обнаружение сервисов и сложные маршрутизационные правила.

- Безопасное хранение конфигураций: Использование ConfigMaps и Secrets в Kubernetes, в сочетании с HashiCorp's Vault для хранения конфиденциальных данных, 
обеспечивает безопасное управление конфигурациями и секретами.

