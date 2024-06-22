# Домашнее задание к занятию 9 «Процессы CI/CD»

## Подготовка к выполнению

1. Создайте два VM в Yandex Cloud с параметрами: 2CPU 4RAM Centos7 (остальное по минимальным требованиям).
2. Пропишите в [inventory](./infrastructure/inventory/cicd/hosts.yml) [playbook](./infrastructure/site.yml) созданные хосты.
3. Добавьте в [files](./infrastructure/files/) файл со своим публичным ключом (id_rsa.pub). Если ключ называется иначе — найдите таску в плейбуке, которая использует id_rsa.pub имя, и исправьте на своё.
4. Запустите playbook, ожидайте успешного завершения.
5. Проверьте готовность SonarQube через [браузер](http://localhost:9000).
6. Зайдите под admin\admin, поменяйте пароль на свой.
7.  Проверьте готовность Nexus через [бразуер](http://localhost:8081).
8. Подключитесь под admin\admin123, поменяйте пароль, сохраните анонимный доступ.

Playbook с первого раза не отработал, так как 11-ая постгра не доступна) Поменял на 12-ую и заработало) 
![Снимок экрана 2024-06-22 в 13 45 13](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/0d11b01b-aa68-43d7-9a50-a3efe180ca49)

SonarType: 

![Снимок экрана 2024-06-22 в 13 48 55](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/4d1f32ed-1170-4784-b1c1-9e6e4998e4ea)

SonarQube: 

![Снимок экрана 2024-06-22 в 13 49 04](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/1c2b2a33-254f-4e18-8cda-5447978de2d1)

## Знакомоство с SonarQube

### Основная часть

1. Создайте новый проект, название произвольное.
2. Скачайте пакет sonar-scanner, который вам предлагает скачать SonarQube.
3. Сделайте так, чтобы binary был доступен через вызов в shell (или поменяйте переменную PATH, или любой другой, удобный вам способ).
4. Проверьте `sonar-scanner --version`.
5. Запустите анализатор против кода из директории [example](./example) с дополнительным ключом `-Dsonar.coverage.exclusions=fail.py`.
6. Посмотрите результат в интерфейсе.
7. Исправьте ошибки, которые он выявил, включая warnings.
8. Запустите анализатор повторно — проверьте, что QG пройдены успешно.
9. Сделайте скриншот успешного прохождения анализа, приложите к решению ДЗ.

Sonar-scaner на месте: 

![Снимок экрана 2024-06-22 в 13 58 06](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/3957c85c-4c5e-47c1-8efa-c6b682d4c2ea)

Первый прогон:

![Снимок экрана 2024-06-22 в 14 05 37](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/b1f4758d-731c-4e56-80b8-58c9230d3407)


Второй:

![Снимок экрана 2024-06-22 в 14 13 27](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/1151e869-99b4-4507-a1b4-ad2c4820fd3b)




## Знакомство с Nexus

### Основная часть

1. В репозиторий `maven-public` загрузите артефакт с GAV-параметрами:

 *    groupId: netology;
 *    artifactId: java;
 *    version: 8_282;
 *    classifier: distrib;
 *    type: tar.gz.
   
2. В него же загрузите такой же артефакт, но с version: 8_102.
3. Проверьте, что все файлы загрузились успешно.
4. В ответе пришлите файл `maven-metadata.xml` для этого артефекта.

Ссылка [тут](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/09-ci-03-cicd/mvn/maven-metadata.xml)

### Знакомство с Maven

### Подготовка к выполнению

1. Скачайте дистрибутив с [maven](https://maven.apache.org/download.cgi).
2. Разархивируйте, сделайте так, чтобы binary был доступен через вызов в shell (или поменяйте переменную PATH, или любой другой, удобный вам способ).
3. Удалите из `apache-maven-<version>/conf/settings.xml` упоминание о правиле, отвергающем HTTP- соединение — раздел mirrors —> id: my-repository-http-unblocker.
4. Проверьте `mvn --version`.
5. Заберите директорию [mvn](./mvn) с pom.

### Основная часть

1. Поменяйте в `pom.xml` блок с зависимостями под ваш артефакт из первого пункта задания для Nexus (java с версией 8_282).
2. Запустите команду `mvn package` в директории с `pom.xml`, ожидайте успешного окончания.
3. Проверьте директорию `~/.m2/repository/`, найдите ваш артефакт.
4. В ответе пришлите исправленный файл `pom.xml`.

Билд успешно отработал: 

![Снимок экрана 2024-06-22 в 15 41 08](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/93bbacd5-0fb8-42ee-adb7-3bc1e7fde36a)

Локально все на месте: 

![Снимок экрана 2024-06-22 в 15 42 50](https://github.com/alexandreevich/mnt-homeworks/assets/109306886/cd093344-1fb2-4632-b971-28faac361789)


Ссылка на pom [тут](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/09-ci-03-cicd/mvn/pom.xml)

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
