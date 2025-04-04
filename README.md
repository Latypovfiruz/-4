# автономный автобус.
Описание применения и назначения краткое продукта:.

Бесконтактной на с проезда основе биометрии. автономный оплатой продукт - автобус.

После сканирует пассажира лицо автобус оплату входе и идентификации. на проводит.

![image](https://github.com/user-attachments/assets/a9ed372a-a1fa-486d-8511-f23937d3a2d5).

**преимущества:**.

Снижение и затрат на (нет кассиров валидаторов). ✔ обслуживание.

✔ ускорение посадки за счет автоматизированного процесса.

✔ гигиеничность (минимум касаний поверхностей).

Системами. приложениями с интеграция банковскими мобильными ✔ и.

**роли пользователей**.

Оператор системы - вводит информацию о маршрутах.

Системы перед - выходом автобуса проверяет депо сотрудник маршрут на.

Пассажиры - перемещаются в автобусе согласно маршруту.

Ценности, неприемлемые события ущербы, ключевые.


### Ключевые ценности, риски и неприемлемые события для автономного автобуса с биометрической оплатой

| Ценность                | Негативное событие                                                                 | Уровень ущерба | Комментарий                                                                 |
|-------------------------|-----------------------------------------------------------------------------------|----------------|-----------------------------------------------------------------------------|
| **Безопасность**        | Ложное срабатывание биометрии (пропуск постороннего/отказ законному пассажиру)    | Высокий        | Риск конфликтов, задержек, подрыв доверия к системе                        |
| **Конфиденциальность**  | Утечка биометрических данных (лиц, платежной информации)                          | Критический    | Юридические последствия, репутационный ущерб, штрафы по GDPR/152-ФЗ        |
| **Надежность системы**  | Сбой оплаты (ошибка сканера/транзакции)                                           | Средний        | Прерывание работы → бесплатный проезд или остановка транспорта             |
| **Скорость посадки**    | Задержки из-за медленного распознавания                                           | Средний        | Образование очередей, недовольство пассажиров                             |
| **Автономность**        | Отказ системы навигации (ошибки маршрута/распознавания препятствий)               | Высокий        | Риск ДТП, необходимость ручного вмешательства                              |




![mermaid-diagram-2025-03-30-231847](https://github.com/user-attachments/assets/3585e61a-b1ad-4296-96cf-c1fe775894cb).


**основные функциональные сценарии**.

![image](https://github.com/user-attachments/assets/d48b4842-3e52-4429-8137-b96aa53c401d).


Архитектура**

![image](https://github.com/user-attachments/assets/5ec76da5-0311-46b0-8c01-d9e7cd111656).
| Подсистема    | Назначение                                                                | Компоненты / Функции                                                              |
|--------------|---------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| **Пассажир**  | Инициатор процесса: использует систему для входа в автобус               | • Сканирование лица через терминал <br>• Взаимодействие с системой доступа       |
| **Биометрия** | Идентификация пользователя по лицу                                       | • HD-камеры с ИК-подсветкой <br>• FaceNet для распознавания <br>• Liveness Check |
| **Платежи**   | Проведение транзакций и управление доступом                             | • Проверка баланса в реальном времени <br>• Оффлайн-кеш на 100 транзакций        |
| **Банк**      | Подтверждение платежей и обработка финансовых операций                  | • REST API с поддержкой PSD2 <br>• Система анализа мошеннических транзакций      |
| **Управление**| Контроль физических систем автобуса                                     | • CAN-шина для управления дверьми <br>• Датчики безопасности (блокировка при движении) |
| **Двери**     | Механизм управления доступом                                           | • Электропривод 24V <br>• Аварийный ручной размыкатель                           |
| **Сеть**      | Связь и передача данных между компонентами                             | • 5G/LTE-модем с dual-SIM <br>• Локальное хранилище логов (SQLite)               |

Сценариев** функциональных диаграммы **расширенные.
Высокоуровневой указанных в подсистем, архитектуре иллюстрация взаимодействия.

![image](https://github.com/user-attachments/assets/8c413de1-7dc2-4e6a-91a6-3ab52eaf8e54).

Безопасности предположения цели.

Безопасности** **цели.
1. данных - всех шифрование этапах и хранения; конфиденциальность данных на передачи.
2. целостность операций - предотвращение подмены биометрических идентификаторо  и гарантия неизменности транзакций и логируемых событий;.
Компонентов системы работа критических оффлайн-режиме; резервирование доступность - 3. в.
4. аутентичность пользователей - защита от поддельных биометрических данных;.
   
**предположения безопасности**.
1. шифрование данных - используемые алгоритмы (aes-256, гост р 34.12-2015) соответствуют стандартам;.
2. сетевая - связи; инфраструктура каналов защиту.
3. обслуживание по регулярное.
Оборудования и банка - 4. физическая защита.

**Таблица соотнесения ценностей, неприемлемых событий и целей безопасности**

| Ценность                      | событие                                 | Оценка ущерба | Цель безопасности                          |
|-------------------------------|------------------------------------------|---------------|--------------------------------------------|
| **Биометрические данные**     | Утечка/кража биометрических шаблонов     | Высокий       | Конфиденциальность, Аутентичность          |
| **Платежные транзакции**      | Подмена/отмена транзакций                | Высокий       | Целостность, Неотказуемость               |
| **Доступность автобуса**      | DDoS-атака на сетевой модуль             | Средний       | Доступность, Резервирование               |
| **Физические механизмы**      | Несанкционированное открытие/блокировка  | Критический   | Контроль доступа, Аутентичность           |
| **Логи операций**             | Фальсификация/удаление записей           | Средний       | Целостность, Неотказуемость               |
| **Пользовательский интерфейс**| Фишинг/ввод ложных данных                | Низкий        | -  |



**негативные сценарии**.

![image](https://github.com/user-attachments/assets/7c14de86-e0ec-43c1-9e9b-c0bc72946afc).

**Архитектуры** **политика.**

![mermaid-diagram-2025-03-30-225150](https://github.com/user-attachments/assets/51129fe5-1657-4c84-87f0-d0cacb164c20).


# Таблица доменов безопасности системы
| Домен        | Уровень доверия            | Оценка сложности и размера | Обоснование                                                              |
|--------------|---------------------------|----------------------------|--------------------------------------------------------------------------|
| **Пассажир**  | Недоверенная сущность     | S, S                       | Внешний пользователь, минимальный контроль над входными данными         |
| **Биометрия** | Доверенная сущность       | C, L                       | Критически важный компонент с алгоритмами ИИ и требованиями к точности  |
| **Платежи**   | Доверенная сущность       | M, M                       | Ядро финансовых операций, интеграция с банковскими API                  |
| **Банк**      | Доверенная+ (целостность) | C, XL                      | Внешняя система с высокими требованиями к безопасности и надежности     |
| **Управление**| Частично доверенная       | M, M                       | Физические системы управления, возможны аппаратные сбои и атаки         |
| **Двери**     | Недоверенная сущность     | S, S                       | Простая механическая система с минимальной логикой                      |
| **Сеть**      | Частично доверенная       | M, L                       | Внешние коммуникации, потенциально уязвима к атакам                     |

