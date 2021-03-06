# Тестирование отказоустойчивого кластера Windows

Рассмотрим два основных варианта запуска тестирования серверов на возможность разворачивания кластера Windows.

## Диспетчер отказоустойчивости кластеров

1. Откроем диспетчер отказоустойчивости кластеров через "Панель управления -> Администрирование".

![Диспетчер отказоустойчивости кластеров](media/2.%20Тестирование%20WSFC/1.%20Запуск%20диспетчека%20WSFC.PNG)

2. Запускаем проверку кластера.

![Запуск проверки кластера](media/2.%20Тестирование%20WSFC/2.%20Запуск%20проверки.PNG)

3. Видим начальную страницу "Мастера проверки конфигурации", нажимаем "Далее".

![Мастер проверки конфигурации](media/2.%20Тестирование%20WSFC/3.%20Начало%20мастера%20проверки.PNG)

4. Выбираем сервера для проверки, которые потом должны войти в состав кластера.

![Сервера для проверки](media/2.%20Тестирование%20WSFC/4.%20Добавляем%20список%20серверов%20для%20проверки.PNG)

5. Подтверждаем настройки и запускаем тестирование.

![Подтверждение параметров тестирования](media/2.%20Тестирование%20WSFC/6.%20Подтверждение%20проверки.PNG)

6. Ожидаем окончания проверки.

![Процесс проверки узлов кластера](media/2.%20Тестирование%20WSFC/7.%20Процесс%20проверки.PNG)

7. Изучаем результаты проверки кластера на предупреждения и критические ошибки. Результат можно изучить как в том же окне, так и открыть отдельный отчет в виде HTML-страницы.

![Результаты проверки конфигурации кластера](media/2.%20Тестирование%20WSFC/8.%20Результат%20проверки.PNG)

Теперь рассмотрим те же самые действия с помощью PowerShell.

## PowerShell

С помощью PS проверку кластера выполнить достаточно просто.

```PowerShell
# С помощью параметра "Node" перечисляем через запятую
# имена серверов, которые будут выступать узлами кластера
Test-Cluster -Node "SQL-AG-1", "SQL-AG-2"
```

Выглядеть это будет так:

1. Готовим команду и запускаем.

![Готовим команду](media/2.%20Тестирование%20WSFC/PowerShell/0.%20PS.%20Команда%20проверки%20кластера.PNG)

2. Ожидаем завершения тестирования.

![Ожидаем завершения проверки](media/2.%20Тестирование%20WSFC/PowerShell/1.%20PS.%20Тест%20кластера.PNG)

3. Смотрим результат.

![Результат проверки](media/2.%20Тестирование%20WSFC/PowerShell/2.%20PS.%20Результат%20проверки%20кластера.PNG)

4. Полная информация о результатах проверки в отчете (см. вывод команды в пункте 3, там путь к отчету).

![Отчет о проверке с подробной информацией](media/2.%20Тестирование%20WSFC/PowerShell/3.%20PS.%20Отчет%20HTML%20о%20проверке%20кластера.PNG)

На этом все. Если проверки пройдены, то можно перейти непосредственно к созданию и настройке кластера.