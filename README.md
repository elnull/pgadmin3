This text Russian language.
English version issue #18

Данные проект поддерживает pgAdmin3 v1.22
Поддержка добавляется по мере возникновения ошибок в оригинальной версии v1.22 или если эти возможности нужны мне.
На 10.10.2018 измененены около 70 исходных файлов.

Только 32 битная версия и только для Windows
для удобства последний скомпилированный исполняемый файл будет находиться в каталоге Release.
Для работы достаточно заменить оригинальный pgAdmin3.exe.

Будет поддерживаться только оригинальная версия PostgreSQL 12 и PostrgesPro Enterprise.

Полная версия pgAdmin3 находиться тут https://github.com/postgres/pgadmin3.git

Что добавлено:
 - Экспорт результата запроса в Excel
 - Добавлен выбор запроса на исполнение под курсором (Auto-Select)
 - Добавлена настраиваемая автозамена (в меню Правка -> Manage autoreplace)
 - Добавлено автосохранение содержимого закладки после выполнения запроса
 - Добавлена возможность задать имя для закладки и возможность сделать закладку автозагружаемой для конкретной БД

 - Добавлена поддержка процедур
 - Добавлена поддержка секционирования (только отображение в дереве объектов)

 - Удалено отображение узлов имеющих статус (Never execute) на закладке графического плана, но в табличном виде они присутствуют.

01.11.2018
 - Добавлено отображение publications.
 - Добавлено изменение фона при при не закоммиченой транзакции.
 - У Commit/Rollback измененены горячие клавиши

11.12.2018
 - Добавлен поиск в дереве по F4 выделеного текста и если объект найден то его открытие.
   Если запрос длится более 2 минут то после завершения запроса окно будет мигать.
 - При открытия функции фокус устанавливается сразу на закладку Код.

05.12.2018
 - Добавлена поддержка расширения pgpro_scheduler
   В разделе Статистика отображается информация о последнем отработавшем задании.
   Инфомация берётся из лог таблицы pg_log при условии что таблица существует и видна, установлен флаг "Enabled ASUTP style"
   выводиться результат запроса: select log_time,detail critical,message,application_name from pg_log l where l.log_time>'$Started'::timestamp - interval '1min' and l.log_time<'$Finised' and hint='$name'
 - В выводе результатов запроса ячейки со значениям содержащие символ перевода строки \n подсвечиваются
 * В экспорте результатов запроса в Excel исправлена ошибка при сохранении интервалов
 * При обновлении схемы не блокируется интерфейс если на таблице идет долгая операция cluster
   Но при F5 на самой таблице блокировка сохраняется (это связано с блокированием функций pg_def* при получинии информации от таблицах)
09.12.2018
 - autocomplite: добавлены имена функций, и возможность подставлять имена колонок таблиц из поля FROM
 - при наборе имени функции появляется перечень параметров этой функции

28.12.2018
 - выполнен переход на wxWidgets 3.0 версия exe файла будет находиться Release_(3.0)
 - в текстовом представлении плана можно сворачивать узлы
 - построении плана с замерами в заголовках строк указывается процент времени выполнения узла (только операции узла, но не вложенных узлов)


11.01.2019
 - исправлены падения приложения при открытии таблицы по нажатию F4

26.01.2019
 - исправлены падения приложения при вводе ( в окне редактирования кода)
 - ускорено открытие диалога "новая функция", "новая таблицы".

09.02.2019
 - исправлены некторые ошибки
 - добавлено копирование sql в html формате(с сохранением цвета)
 - в вывод SQL инструкций для таблиц добавлен закомментированый перечень колонок с типами

11.03.2019
 - исправлено отображение foreign table

10.09.2019 
 Окно Server Status

 * исправлено падение окна Server Status при аварийном завершении СУБД
 - добавлена расцветка процессов которые блокируют другие процессы

 Окно Query

 - добавлен фильтр в окно результатов запроса. Активируется двойным щелчком мыши по ячейке, текст которой и будет являтся условием фильтра. Снимается из контекстного меню.
   При нажатом Alt условие отбора инвертируется (Скрыть строки содержащие значение).
 - Для избегания ожиданий при получении информации об объектах. Выставляется клиентский параметр SET lock_timeout=15000 для служебного соединения.

04.09.2019
 - добавлена поддержка PostgreSQL 12
 - добавлена поддержка отображения дополнительных опция для индексов
 - в окне запросов добавлена альтернативная кнопка отражающая текущий режим, Transaction (T) или AutoCommit (A)
 * исправлена ошибка в окне поиска объектов при поиске в коментариях

22.12.2019
 - добавлена возможность выполнять сравнение описания объектов разных серверов через меню Отчеты "Compare other objects"
   Сравнение проводится с другим открытым соединением и подключенной базой. Объекты для сравнения выбираются по дереву вниз.
   По результатам формируется html отчет различий. 
   В качестве шаблона для отчета используется файл textcompare_report.template, находящийся рядом с исполняемым pgadmin3.exe.
   Особенности: SQL текст создания последовательностей игнорируется, секции таблиц не учитываются. Полность одинаковые объекты скрываются. Служебные объекты игнорируются.
 - выполнен переход на новые библиотеки dll wxWidgets 3.0.4 скомпилированные под VS2012. Необходимо обновить файлы *.dll
 
04.03.2020
 - добавлен вывод CREATE STATISTICS для таблиц
 * исправлен вывод SQL команды для создания задания для комманд заданных в виде массива

28.03.2020
 - добавлена информация о фрагментации таблицы (cfs_fragmentation)
 * убрано предупреждение о версии сервера

11.04.2020
 - добавлена многоколоночная сортировка результатов выполнения запроса. Порядок сортировки колонок и направление отмечается цветными индикаторами (RED,YELLOW,GREEN,BLUE,GREY).
   Максимальное число колонок сортировки 5. Для выполнения сортировки нужно щелкнуть по заголовку колонки удерживая клавишу Alt.
 - добавлены новые опции для Vaccum ( DISABLE_PAGE_SKIPPING ) и Reindex ( CONCURRENTLY )
 * ускорена работа фильтра в окне результав запроса.

13.04.2020
 * исправлено падение в режиме редактирования
 * исправлено редактирование процедур без аргументов

15.04.2020
 * в окне SQL инструкции создания таблицы теперь отображаются новые параметры хранения
 * в описании колонок учтены generated и identity колонки

22.04.2020
 - добавлена возможность создавать дополнительные окна для вывода результатов запроса (не более 9).
   Для этого запрос нужно выполнить по нажатию Shift+F8.  Вывод результатов при выполнении F8 производиться в текущую активную закладку.
   Окна вывода отмечаются белым квадратом если они были использованы текущей закладкой запросов.
 - при щелчке правой кнопкой мыши на активной закладке результатов в окне запросов выделяется запрос связанный с этим результатом.
 - в окне запросов последний выполненый запрос отмечается зелеными стрелками.
 - при автосохранении закладок, сохраняется позиция курсора

06.05.2020
 * исправлена проблема #4 (Crash after close sql editor)
  
08.05.2020
 * исправлена проблема #6 (Child tables are not dispayed). Отображение секций из других схем нарушает строгую иерархичность обектов 
   и нужно убедиться что всё нормально в вашем случае. Секции всегда группируются в узел Partitions который находиться в родительской таблице.
   В родной схеме, секции как таблицы увидеть нельзя.
 * мелкие улучшения

19.08.2021
 - добавлено окно просмотра CSV лога базы.
   Окно вызывается из контекстного меню сервера "Log view ...".
   
   После открытия окна читается непосредственно файл лога функцией pg_read_binary_file
   Выбирается файл с самой свежей датой изменения. Проверка новых сообщений проводиться каждые 5 секунд.
   Можно добавить другие сервера на панели "Settings". Настройки применяются после закрытия окна и повторного его открытия.
   Если окно лога не активное и приходит сообщения уровня Error и выше, то иконка отмечается красным квадратом.
   Если на заладке "Settings" выбрано несколько серверов, то происходить автоматическое подключение к ним.
   После подключения все открытые сервера в дереве объектов можно закрыть одной командой контекстного меню 
   "Disconnect all servers".
   ВНИМАНИЕ: память требуемая для хранения логов ни чем не ограничивается (кроме фильтрации на этапе загрузки лога) и 
   возможно выделения большого количества памяти.
   Отображаются строки лога в двух режимах:
   * Простой. Отобразаются все полученные строки лога
   * Групповой. Строки с похожими сообщениями объединяются в группу и видимой строкой является самая последняя строка
     в группе. Для просмотра всех строк группы нужно установить флаг "View detail group".
     Сообщения будут похожими если они отличаются только числами и если они не в двойных кавычках.
     В групповом режиме в поле host показываются счетчик свежих сообщений попавших в группу. Счетчик сбрасывается при 
     установке курсора на строку группы.
   Для исключения из просмотра ненужных строк используются поколоночные фильтры. Для включения фильтра нужно:
   * Щелкнуть правой кнопкой мыши по полю. Для инверсии фильтра нужно удерживать Ctrl.
   * Выбрать значение в контекстном меню заголовка колонки. Там отображаются 20 самых частых значения в колонке с указанием
     количества этих значений.
   * Ввести в поле значения для фильтра, выделить это значение и нажать Enter. Для фильтра используется только выделенный 
     текст. Такой фильтр будет работать на поиск выделенного вхождения в поле. Если в выделенной строке 
     первым символом будет "!" то фильтер инверсируется.
   * каждое отдельное значение фильтра можно удалить через контекстное меню заголовка колонки.
     Для более высокой производительности рекомендуется проводить загрузку логов с включенным "Mode group".
     Или сбрасывать "Mode group", но при установленных фильтрах.
     Отображение большого число строк (более 10000 ) происходит несколько секунд и более.
   * Есть возможность отсеять строки на этапе загрузки. Для этого установите фильтры на строки и нажмите
     "Add Filter Ignore" этот фильтр будет записан в файл filter_load.txt.

13.09.2021
 - Добавлено меню закрытия всех открытых серверов "Disconnect all servers"
 - 
   
   




 

