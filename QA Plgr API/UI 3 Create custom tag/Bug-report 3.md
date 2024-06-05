# Bug-report 3

## Сортировка по созданному тегу на странице “Contacts” не работает

### Описание

После создания нового тега для выбранного в списке контакта, сортировка по новому тегу не срабатывает. На странице “Contacts”отсортированный список контактов отображается пустым. 

### **Предусловия**

Открыть страницу [**https://dev-crm.qa-playground.com**](https://dev-crm.qa-playground.com/)

### Шаги

1. Перейти во вкладку “Contacts”
2. На странице “Contacts” выбрать любого клиента и кликнуть на его карточку
3. Найти раздел “Tags” в правой боковой панели
4. Нажать на кнопку “Add tags”, чтобы открыть меню тегов
5. В выпадающем списке меню нажать на кнопку “Create a new tag”
6. В текстовом поле “Tag name” ввести следующее (включая спецсимволы): “@#new—-tag”|\
7. Нажать на кнопку “Add tag”, чтобы добавить тег к выбранному контакту
8. Перейти во вкладку “Contacts”
9. В левой части экрана под строкой поиска найти блок “TAGS”
10. В списке найти созданный тег “@#new—-tag”|\ и кликнуть на него, чтобы отсортировать список контактов

### Ожидаемый результат

На странице “Contacts” происходит сортировка и в центральной части экрана появляется список контактов, которым присвоен тег  “@#new—-tag”|\

### Фактический результат

На странице “Contacts” сортировка не происходит. Список контактов с созданным тегом отображается пустым

### Окружение

Яндекс Браузер Версия 24.4.3.1086 (64-bit)

Windows 11 Pro 10.0.22631

### Приоритет

P1 - Высокий. Функция сортировки клиентов по созданным тегам является важной для эффективной работы, но ее неработоспособность не блокирует основной функционал системы. Менеджеры могут использовать другие пути поиска клиентов

### Серьезность

S2 - Критическая. Ошибка в функциональности системы, которая мешает менеджерам по продажам осуществлять поиск по вновь созданным тегам, может привести к снижению скорости и эффективности работы.

### Приложение

Шаг 10.

![Untitled](Bug-report%203%2070b042836c394836a3cb25f72700eb32/Untitled.png)