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








