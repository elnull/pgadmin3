This text Russian language.

Данные проект поддерживает pgAdmin3 v1.22
Поддержка добавляется по мере возникновения ошибок в оригинальной версии v1.22 или если эти возможности нужны мне.
На 10.10.2018 измененены около 70 исходных файлов.

Только 32 битная версия и только для Windows
для удобства последний скомпилированный исполняемый файл будет находиться в каталоге Release.
Для работы достаточно заменить оригинальный pgAdmin3.exe.

Будет поддерживаться только оригинальная версия PostgreSQL 11.

Полная версия pgAdmin3 находиться тут https://github.com/postgres/pgadmin3.git

Что добавлено:
Экспорт результата запроса в Excel
Добавлен выбор запроса на исполнение под курсором (Auto-Select)
Добавлена настраиваемая автозамена (в меню Правка -> Manage autoreplace)
Добавлено автосохранение содержимого закладки после выполнения запроса
Добавлена возможность задать имя для закладки и возможность сделать закладку автозагружаемой для конкретной БД

Добавлена поддержка процедур
Добавлена поддержка секционирования (только отображение в дереве объектов)

Удалено отображение узлов имеющих статус (Never execute) на закладке графического плана, но в табличном виде они присутствуют.

01.11.2018
Добавлено отображение publications
Добавлено изменение фона при при не закоммиченой транзакции
У Commit/Rollback измененены горячие клавиши
