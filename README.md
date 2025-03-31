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


**контекст**.

![mermaid-diagram-2025-03-30-231847](https://github.com/user-attachments/assets/3585e61a-b1ad-4296-96cf-c1fe775894cb).


**основные функциональные сценарии**.

![image](https://github.com/user-attachments/assets/d48b4842-3e52-4429-8137-b96aa53c401d).


Архитектура** **высокоуровневая.

![image](https://github.com/user-attachments/assets/5ec76da5-0311-46b0-8c01-d9e7cd111656).

Подсистемы ##.

| назначение | | подсистема компоненты/функции |.
|--------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|.
| **пассажир** | инициатор процесса: использует сервис для входа в автобус                  | • сканирование лица через терминал<br>• взаимодействие с системой доступа         |.
| **биометрия** | идентификация пользователя по лицу                                         | • hd-камеры с ик-подсветкой<br>• facenet для распознавания<br>• liveness check    |.
В баланса доступом оффлайн-кеш **платежи** | | управление • | проведение реальном транзакции на 100 транзакций времени<br>• проверка и |.
| **банк**     | подтверждение платежей и обработка финансовых операций                     | • rest api с psd2-совместимостью<br>• система анализа мошенничества               |.
| **управление** | контроль физических систем автобуса                                       | • can-шина для управления дверьми<br>• датчики безопасности (закрытие при движении)|.
Аварийный **двери** доступа 24v<br>• | размыкатель | предоставления механизм | ручной • электропривод |.
| **сеть**     | передача данных между компонентами                                         | • 5g/lte модем с dual-sim<br>• локальное хранилище логов (sqlite)                 |.


Сценариев** функциональных диаграммы **расширенные.
Высокоуровневой указанных в подсистем, архитектуре иллюстрация взаимодействия.

![image](https://github.com/user-attachments/assets/8c413de1-7dc2-4e6a-91a6-3ab52eaf8e54).

Безопасности** предположения **цели и.

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

**таблица соотнесения ценностей, неприемлемых событий и целей безопасности**.

| | цель ценность | | оценка неприемлемое безопасности событие | ущерба.
|-------------------------------|------------------------------------------|---------------|--------------------------------------------|.
| **биометрические данные**     | утечка/кража биометрических шаблонов     | высокий       | конфиденциальность, аутентичность          |.
| | подмена/отмена неотказуемость | транзакций высокий транзакции** целостность, | **платежные |.
Резервирование ddos-атака | | на | средний | автобуса** модуль **доступность сетевой | доступность,.
Критический механизмы** | | | | открытие/блокировка аутентичность **физические несанкционированное контроль | доступа,.
| | | целостность, средний записей операций** | | неотказуемость **логи фальсификация/удаление.
| **пользовательский интерфейс**| фишинг/ввод ложных данных                | низкий        | -  |.


**негативные сценарии**.

![image](https://github.com/user-attachments/assets/7c14de86-e0ec-43c1-9e9b-c0bc72946afc).

Архитектуры** **политика.

![mermaid-diagram-2025-03-30-225150](https://github.com/user-attachments/assets/51129fe5-1657-4c84-87f0-d0cacb164c20).

# таблица доменов безопасности системы.
# Таблица доменов безопасности системы

| Домен безопасности       | Уровень доверия           | Оценка сложности и размера | Обоснование                                                                 |
|--------------------------|---------------------------|----------------------------|-----------------------------------------------------------------------------|
| **Пассажир**             | Недоверенная сущность     | [S, S]                     | Внешний пользователь, минимальный контроль над входными данными            |
| **Биометрия**            | Доверенная сущность       | [C, L]                     | Критичный компонент с алгоритмами ИИ      |
| **Платежи**              | Доверенная сущность       | [M, M]                     | Ядро финансовых операций, интеграция с API                |
| **Банк**                 | Доверенная+ (целостность) | [C, XL]                    | Внешняя система с высочайшими требованиями к безопасности    |
| **Управление**           | Недоверенная сущность     | [M, M]                     | Физические системы управления, потенциал для аппаратных сбоев             |
| **Двери**                | Недоверенная сущность     | [S, S]                     | Простая механика, минимальная логика                       |
| **Сеть**                 | Недоверенная сущность     | [M, L]                     | Внешние коммуникации, уязвима к атакам    |



