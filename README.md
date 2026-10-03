# mephi-linux-security-2026
В рамках данного домашнего задания в операционной системе **РЕД ОС** (на базе GNU/Linux) были изучены и практически реализованы базовые механизмы дискреционного управления доступом (DAC), администрирования пользователей, мониторинга системных объектов, а также современные методы безопасного повышения привилегий через механизмы `set-UID`, `capabilities` и `sudo`.

## Таблица выполнения разделов

| Раздел | Наименование задания | Статус / Описание реализации | Артефакты / Файлы |
| :--- | :--- | :--- | :--- |
| **1** | Создание пользователя | Создан пользователь `user1` с UID `1234`, добавлен в группу `students`, настроен срок действия пароля каждые 90 дней.<br><br><img width="932" alt="1" src="https://github.com/user-attachments/assets/36943a49-0265-4585-a0f1-c8351a44dc8a" /> | `/etc/passwd`, `/etc/shadow`, `/etc/group` |
| **2** | Мониторинг файлов и процессов | Выполнен поиск всех файлов с установленным битом `set-UID` и отслежены процессы с повышенными привилегиями (`EUID = 0`).<br><br><img width="923" alt="2 1" src="https://github.com/user-attachments/assets/755c247c-eeaa-4b9f-97d9-ca0e2355e9c5" /> | `suid_files.out`, `escalated_procs.out` |
| **3** | Изучение механизма `set-UID` | Скопирована утилита `cat` в домашнюю директорию (`~/mycat`), установлен владелец `root` и бит `SUID`. Проверено чтение защищенного файла `/etc/shadow`.<br><br><img width="920" alt="3" src="https://github.com/user-attachments/assets/f6e40c87-2f75-4f43-beb4-bb3d0a055096" /> | `stat.out`, `history.out` |
| **4** | Изучение механизма привилегий | Скопирована утилита `cat` (`~/mycat_cap`), с помощью `setcap` назначена привилегия `cap_dac_read_search=ep`. Проверен обход ограничений DAC.<br><br><img width="920" alt="4" src="https://github.com/user-attachments/assets/d6b5c6af-b978-4974-b53d-c2d76a20cf4a" /> | `getcap.out`, `stat.out` |
| **5** | Изучение механизма `sudo` | В конфигурационном файле `/etc/sudoers` через `visudo` настроено право для пользователя `user1` на изменение системного времени.<br><br><img width="916" alt="5_2" src="https://github.com/user-attachments/assets/4069da54-b938-4e4d-8c6b-4d65b734116e" /><br><br><img width="920" alt="5_3" src="https://github.com/user-attachments/assets/9d47248f-e945-4ad2-baf0-f085de738ca3" /> | `/etc/sudoers` |
| **6** | Сбор артефактов | Сделан скриншот экрана, сохранена история команд и выводы диагностических утилит.<br><br><img width="1278" alt="mephi-screenshot" src="https://github.com/user-attachments/assets/9413ece1-8550-47e6-99d1-eb2fa6e06a1e" /> | `mephi-screenshot.png`, `history.out`, `stat.out`, `getcap.out` |
| **7** | Публикация на GitHub | Создан публичный репозиторий `mephi-linux-security-2026`, загружены все необходимые файлы и документация. | Ссылка на репозиторий |

---

## Структура репозитория
* `mephi-screenshot.png` — визуальное подтверждение выполнения работы со студенческим идентификатором.
* `history.out` — история команд, выполненных в терминале.
* `stat.out` — информация о правах и метаданных домашней директории и тестовых утилит.
* `getcap.out` — проверка установленных файловых привилегий.
* `suid_files.out` — результаты сканирования SUID-файлов в системе.
* `escalated_procs.out` — результаты мониторинга привилегированных процессов.
* Конфигурационные файлы: `passwd`, `shadow`, `group`, `sudoers`.
