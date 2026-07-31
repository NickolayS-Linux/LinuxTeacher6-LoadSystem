# LinuxTeacher6-LoadSystem

Работа с загрузчиком, ДЗ №6

Создал аккаунт на GitHub - https://github.com/

Предварительно установленное и настроенное следующее ПО:

ПК на Linux c 16 ГБ ОЗУ или виртуальная машина с системой Ubuntu.

Oracle VirtualBox (https://www.virtualbox.org/wiki/Linux_Downloads).

Все дальнейшие действия были проверены при использовании VirtualBox 7.2.6 r172322, хостовая ОС: Ubuntu 24.04 Desktop.

Гостевая система — Ubuntu 24.04.4 LTS. (Сервер и клиент

Оформить отчет в README-файле в GitHub-репозитории.

Цель:

* Включить отображение меню Grub.

* Попасть в систему без пароля несколькими способами.
 
* Установить систему с LVM, после чего переименовать VG.

**Включить отображение меню Grub**

По умолчанию меню загрузчика Grub скрыто и нет задержки при загрузке. 

По умолчанию как видим GRUB_TIMEOUT = 0

<img width="815" height="691" alt="image" src="https://github.com/user-attachments/assets/e135471f-0283-4345-bc87-710dee65f850" />

Для отображения меню нужно отредактировать конфигурационный файл.

Выставлю таймаут 30 сек:

<img width="771" height="675" alt="image" src="https://github.com/user-attachments/assets/50b06209-ff95-4a05-b9d0-817c6a41ea41" />

Выполню обновление загрузчика:

<img width="665" height="287" alt="image" src="https://github.com/user-attachments/assets/adfae02b-9f46-4431-ba7d-17cbcaf14c34" />

И перезапущу виртуальную машину:

<img width="610" height="111" alt="image" src="https://github.com/user-attachments/assets/0db34d69-5aab-473b-a099-7417090db46e" />

Экран после изменения загрузчика:

<img width="827" height="625" alt="image" src="https://github.com/user-attachments/assets/5c1ba6a1-65be-48ad-b3ec-4166457e513f" />

**Попасть в систему без пароля несколькими способами**

Для получения доступа необходимо открыть GUI VirtualBox (или другой системы виртуализации), 

запустить виртуальную машину и при выборе ядра для загрузки нажать **e** - в данном контексте edit. 

Попадаем в окно, где мы можем изменить параметры загрузки:

<img width="659" height="509" alt="image" src="https://github.com/user-attachments/assets/24b51519-e318-4840-aa72-9132a4ea9001" />

Способ 1. init=/bin/bash

В конце строки, начинающейся с linux, добавляем init=/bin/bash и нажимаем сtrl-x для загрузки в систему

<img width="774" height="557" alt="image" src="https://github.com/user-attachments/assets/4bc39bc6-fb97-41f5-8f22-6cc0757dfbf8" />

В целом я загрузился и попал в систему:

<img width="663" height="223" alt="image" src="https://github.com/user-attachments/assets/b8e808f0-e68d-43f1-9ab2-10408e647326" />

Рутовая файловая система при этом монтируется в режиме Read-Only. 

<img width="804" height="182" alt="image" src="https://github.com/user-attachments/assets/f20cdd50-cfbf-4552-b3b3-c5807b7d665c" />

Если я хочу перемонтировать ее в режим Read-Write, можно воспользоваться командой:

<img width="779" height="202" alt="image" src="https://github.com/user-attachments/assets/492ded3f-0a1a-4b7d-8162-2bdb386f94f6" />

И создам в домашней папке root файл, check_root.txt, добавлю в него текст:

<img width="410" height="128" alt="image" src="https://github.com/user-attachments/assets/4d0abda3-cdde-4cb9-88d8-a18128a6cbbe" />

Посмотрим, сохранился ли ;)

<img width="440" height="109" alt="image" src="https://github.com/user-attachments/assets/35164524-fe11-47c7-b086-30ec98bb0971" />

Все работает. Ура. ))

Способ 2. Recovery mode

Перезапустим виртуальную машину, чтобы попасть в загрузчик GRUB. и выберу следующее:

<img width="734" height="533" alt="image" src="https://github.com/user-attachments/assets/75542d52-e1d2-4314-8124-e71e79fd0a92" />

И попадаю в следующее подменю:

<img width="757" height="543" alt="image" src="https://github.com/user-attachments/assets/7a85047c-5d73-4c2d-92dd-02a39303e426" />

Выбираю загрузку в режиме Recovery с ядром 6.16.0:

<img width="691" height="509" alt="image" src="https://github.com/user-attachments/assets/589c7189-7601-41b0-8ea9-c299b60c051b" />

Получаю меню режима восстановления

<img width="785" height="468" alt="image" src="https://github.com/user-attachments/assets/cc2a0cec-c870-400c-bb71-86025ac893ed" />

В этом меню сначала включаю поддержку сети (network) для того, чтобы файловая система перемонтировалась в режим read/write 

(либо это можно сделать вручную).

<img width="806" height="531" alt="image" src="https://github.com/user-attachments/assets/850b3287-8228-41ab-9eb8-755d847504ce" />

Выбираю Yes

<img width="790" height="499" alt="image" src="https://github.com/user-attachments/assets/299491a9-11c0-4554-8b09-a5ea829ed6ba" />

Система смонтирована, далее выбираю пункт root и попадаю в консоль с пользователем root. 

<img width="789" height="489" alt="image" src="https://github.com/user-attachments/assets/e7596072-32c3-4584-8777-7c62beec0ae1" />

Ранее устанавливал пароль для пользователя root (по умолчанию его нет), то необходимо его ввести. 



В этой консоли можно производить любые манипуляции с системой.
:

