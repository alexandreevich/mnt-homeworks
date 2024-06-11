# Домашнее задание к занятию 7 «Жизненный цикл ПО»

## Подготовка к выполнению

1. Получить бесплатную версию Jira - https://www.atlassian.com/ru/software/jira/work-management/free (скопируйте ссылку в адресную строку). Вы можете воспользоваться любым(в том числе бесплатным vpn сервисом) если сайт у вас недоступен. Кроме того вы можете скачать [docker образ](https://hub.docker.com/r/atlassian/jira-software/#) и запустить на своем хосте self-managed версию jira.
2. Настроить её для своей команды разработки.
3. Создать доски Kanban и Scrum.
4. [Дополнительные инструкции от разработчика Jira](https://support.atlassian.com/jira-cloud-administration/docs/import-and-export-issue-workflows/).

## Основная часть

Необходимо создать собственные workflow для двух типов задач: bug и остальные типы задач. Задачи типа bug должны проходить жизненный цикл:

1. Open -> On reproduce.
2. On reproduce -> Open, Done reproduce.
3. Done reproduce -> On fix.
4. On fix -> On reproduce, Done fix.
5. Done fix -> On test.
6. On test -> On fix, Done.
7. Done -> Closed, Open.

Остальные задачи должны проходить по упрощённому workflow:

1. Open -> On develop.
2. On develop -> Open, Done develop.
3. Done develop -> On test.
4. On test -> On develop, Done.
5. Done -> Closed, Open.

**Что нужно сделать**

1. Создайте задачу с типом bug, попытайтесь провести его по всему workflow до Done. 
1. Создайте задачу с типом epic, к ней привяжите несколько задач с типом task, проведите их по всему workflow до Done. 
1. При проведении обеих задач по статусам используйте kanban. 
1. Верните задачи в статус Open.
1. Перейдите в Scrum, запланируйте новый спринт, состоящий из задач эпика и одного бага, стартуйте спринт, проведите задачи до состояния Closed. Закройте спринт.
2. Если всё отработалось в рамках ожидания — выгрузите схемы workflow для импорта в XML. Файлы с workflow и скриншоты workflow приложите к решению задания.

---

**Ответ**
Две доски:

![Снимок экрана 2024-05-20 в 15 31 21](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/f29ad9dc-4fcb-4ea6-a6a1-bb467f31945d)


Два вида задач:

![Снимок экрана 2024-05-20 в 16 14 31](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/f75c93ec-fbbd-47f7-9fbb-f166c9292e92)
![Снимок экрана 2024-05-20 в 16 17 18](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/b6d6aac6-83c1-4695-a582-4ec45612c274)


Проведение задачи по воркфлоу:

![Снимок экрана 2024-05-20 в 16 24 33](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/1bf1a6f0-80e2-452c-8fdd-eed47c030afe)


Другой:

![Снимок экрана 2024-05-20 в 16 38 08](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/9fbdcd10-6a34-4681-b61a-f6745a9b5dfa)


Эпик:

![Снимок экрана 2024-05-20 в 17 03 49](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/fde28833-fd97-448b-ac3e-d2d96de3f5c0)


Спринт:

![Снимок экрана 2024-05-20 в 17 04 23](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/1d647366-dd4b-45b2-9386-0d75d85b864f)


Ссылки на xml:

[раз](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/09-ci-01-intro/xml/bug) 

[два](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/09-ci-01-intro/xml/other) 

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
