# Тестирование работы модуля bxmaker.kits

В директории `upload/1c_catalog/` содержатся файлы с тестовыми данными которые нужно разместить 
по такому же пути относительно корня сайта

Файл [bx_1c_import_lite.php](bx_1c_import_lite.php) необходиом разместиььв корне сайта, для ручного импорта.

## Порядок импорта
Порядок импорта при ручном запуске через файл - `bx_1c_import_lite.php`
1. import.xml
2. rests.xml
3. prices.xml
4. offers.xml

> **Важно!**   Файл `offers.xml` содержит описание комплектов. Комплекты создаются 
из простых товаров или торговых предложений. Товары импортированные 
приобретают тип после импорта цен. Поэтому файл нужно импортировать последним, либо делать импорт второй раз.

## Логирование
Для логирования операций можно в файл `bitrix/.setting_extra.php`  добавить логер, нарпимре так
```php
// bitrix/.settings_extra.php
<?
<?php
return array(   
    //....
    'loggers' => [
        'value' => [
            'bxmaker.kits' => [
				'className' => \Bitrix\Main\Diag\FileLogger::class,
				'constructorParams' => [
                    $_SERVER['DOCUMENT_ROOT'].'/logs/bxmaker.kits.txt'
                ],
                'level' => \Psr\Log\LogLevel::DEBUG,
            ],
        ],
        'readonly' => true,
    ],
);
?>
```