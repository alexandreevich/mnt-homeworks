# Домашнее задание к занятию 10 «Jenkins»

## Подготовка к выполнению

1. Создать два VM: для jenkins-master и jenkins-agent.
2. Установить Jenkins при помощи playbook.
3. Запустить и проверить работоспособность.
4. Сделать первоначальную настройку.

## Ответ
ВМ развернуты: 


![Снимок экрана 2024-07-20 в 15 57 01](https://github.com/user-attachments/assets/63b3a839-32f7-4ffe-9ac1-94a4c08b9f3e)

Ansible-playbook отработал корректно:

<img width="1281" alt="Снимок экрана 2024-07-20 в 19 51 13" src="https://github.com/user-attachments/assets/0d4a508b-f6df-4697-a02a-e87250444d7d">


Взаимосвязь master - slave настроена:

![Снимок экрана 2024-07-20 в 15 58 13](https://github.com/user-attachments/assets/970fda77-b308-4f21-aaf4-c91ec29ba4a8)


## Основная часть

1. Сделать Freestyle Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
2. Сделать Declarative Pipeline Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
3. Перенести Declarative Pipeline в репозиторий в файл `Jenkinsfile`.
4. Создать Multibranch Pipeline на запуск `Jenkinsfile` из репозитория.
5. Создать Scripted Pipeline, наполнить его скриптом из [pipeline](./pipeline).
6. Внести необходимые изменения, чтобы Pipeline запускал `ansible-playbook` без флагов `--check --diff`, если не установлен параметр при запуске джобы (prod_run = True). По умолчанию параметр имеет значение False и запускает прогон с флагами `--check --diff`.
7. Проверить работоспособность, исправить ошибки, исправленный Pipeline вложить в репозиторий в файл `ScriptedJenkinsfile`.
8. Отправить ссылку на репозиторий с ролью и Declarative Pipeline и Scripted Pipeline.
9. Сопроводите процесс настройки скриншотами для каждого пункта задания!!

## Ответ

1. Добавил в плейбук: 
<img width="346" alt="Снимок экрана 2024-07-23 в 18 39 27" src="https://github.com/user-attachments/assets/253f681b-15a8-4344-b82f-cdbcd0af8fe0">

Джоба отработала корректно: 

<img width="1107" alt="Снимок экрана 2024-07-20 в 20 53 25" src="https://github.com/user-attachments/assets/10bd2569-30a3-4ce8-a84a-bb1d32710396">

2. Отработал корректно:

```
pipeline {
    agent {
        label 'ansible'
    }
    stages {
        stage('Clear work dir') {
            steps {
                deleteDir()
            }
        }
        stage('Clone git repo') {
            steps {
                dir('vector-role') {
                git branch: 'main', url: 'https://github.com/kibernetiq/vector-role.git'
                }
            }
        }
        stage('Molecule test') {
            steps {
                dir('vector-role') {
                sh 'molecule test'
                }
            }
        }
    }
}
```

<img width="823" alt="Снимок экрана 2024-07-20 в 21 16 34" src="https://github.com/user-attachments/assets/5fa3d5c0-4bd2-4219-bb94-e1de6c777f50">

![Снимок экрана 2024-07-20 в 19 16 24](https://github.com/user-attachments/assets/11dc0501-918f-4387-b59c-9c92ddd9736c)

3. Multibranch Pipeline отработал успешно. 
![FJ_success](https://github.com/user-attachments/assets/e6beb872-413c-4eb9-9e41-274b1c9ad857)

4. Файл добавлен [тут](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/09-ci-04-jenkins/pipeline/ScriptedJenkinsfile) 
Отработал успешно. 


## Необязательная часть

1. Создать скрипт на groovy, который будет собирать все Job, завершившиеся хотя бы раз неуспешно. Добавить скрипт в репозиторий с решением и названием `AllJobFailure.groovy`.
2. Создать Scripted Pipeline так, чтобы он мог сначала запустить через Yandex Cloud CLI необходимое количество инстансов, прописать их в инвентори плейбука и после этого запускать плейбук. Мы должны при нажатии кнопки получить готовую к использованию систему.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
