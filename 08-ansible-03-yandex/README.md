# Домашнее задание к занятию 3 «Использование Ansible»

## Подготовка к выполнению

1. Подготовьте в Yandex Cloud три хоста: для `clickhouse`, для `vector` и для `lighthouse`.
2. Репозиторий LightHouse находится [по ссылке](https://github.com/VKCOM/lighthouse).

## Основная часть

1. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает LightHouse.
2. При создании tasks рекомендую использовать модули: `get_url`, `template`, `yum`, `apt`.
3. Tasks должны: скачать статику LightHouse, установить Nginx или любой другой веб-сервер, настроить его конфиг для открытия LightHouse, запустить веб-сервер.
4. Подготовьте свой inventory-файл `prod.yml`.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.
6. Попробуйте запустить playbook на этом окружении с флагом `--check`.
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги.
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-03-yandex` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---

## Ответ
Плейбук находится по [ссылке](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/08-ansible-03-yandex/site.yml)

IP развернутых в Yandex Cloud вписываются в [инвентарник](https://github.com/alexandreevich/mnt-homeworks/tree/MNT-video/08-ansible-03-yandex/inventory)
На каждый отдельный хост встает соответсвенное ПО. 
Версии ПО можно изменить в файле [group_vars](https://github.com/alexandreevich/mnt-homeworks/tree/MNT-video/08-ansible-03-yandex/group_vars)

Плейбук успешно отрабатывает, прикладываю скриншот: 

![Снимок экрана 2024-05-19 в 12 43 47](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/a27791ae-c681-439f-afd4-7c9bf1cedce5)
