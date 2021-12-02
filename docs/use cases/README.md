# Діаграма прецедентів

@startuml
    actor "Користувач" as User
    actor "Редактор" as Editor
    
    
    usecase "<b>UC_1</b>\nCупроводження даних" as UC_1
    usecase "<b>UC_2</b>\nАрхівація даних" as UC_2
    usecase "<b>UC_3</b>\nВидалення даних" as UC_3
    usecase "<b>UC_4</b>\nПошук даних" as UC_4
    usecase "<b>UC_5</b>\nВідображення даних" as UC_5
    usecase "<b>UC_6</b>\nЗавантаження даних" as UC_6
    usecase "<b>UC_1.1</b>\nДодання даних" as UC_1.1
    usecase "<b>UC_1.2</b>\nРедагування даних" as UC_1.2
    usecase "<b>UC_7</b>\nАвторізація у систему" as UC_7
    usecase "<b>UC_8</b>\nРеєстрація у систему" as UC_8
    usecase "<b>UC_9</b>\nДодання нового редактора" as UC_9
    

    User -u-> UC_4
    User -u-> UC_5
    User -u-> UC_6
    User -r-> UC_7
    User -l-> UC_8
    
    Editor -u-|> User
    
    Editor -d-> UC_1
    Editor -d-> UC_2
    Editor -d-> UC_3
    Editor -r-> UC_9
    UC_1.1 .d.> UC_1: extends
    UC_1.2 .d.> UC_1: extends

    
@enduml

## Модель використання користувача

@startuml

    actor "Користувач" as User
    
  
    usecase "<b>UC_4</b>\nПошук даних" as UC_4
    usecase "<b>UC_5</b>\nВідображення даних" as UC_5
    usecase "<b>UC_6</b>\nЗавантаження даних" as UC_6
    usecase "<b>UC_7</b>\nАвторізація у систему" as UC_7
    usecase "<b>UC_8</b>\nРеєстрація у систему" as UC_8


    User -u-> UC_4
    User -u-> UC_5
    User -u-> UC_6
    User -r-> UC_7
    User -l-> UC_8

    
@enduml

## Модель використання редактора

@startuml
    
    actor "Редактор" as Editor
    
    usecase "<b>UC_1</b>\nCупроводження даних" as UC_1
    usecase "<b>UC_2</b>\nАрхівація даних" as UC_2
    usecase "<b>UC_3</b>\nВидалення даних" as UC_3
    usecase "<b>UC_1.1</b>\nДодання даних" as UC_1.1
    usecase "<b>UC_1.2</b>\nРедагування даних" as UC_1.2
    usecase "<b>UC_9</b>\nДодання нового редактора" as UC_9

    
    Editor -u-> UC_1
    Editor -u-> UC_2
    Editor -u-> UC_3
    Editor -r-> UC_9
    UC_1.1 .u.> UC_1: extends
    UC_1.2 .u.> UC_1: extends

    
@enduml

# Сценарії 

### 3.1 Додання даних

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-1.1
        <font color=000 size=16><b>Назва:</b> Додання даних
        <font color=000 size=16><b>Учасники:</b> Редактор, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Редактор, нові дані
        <font color=000 size=16><b>Результат:</b> Додання даних
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16>EX-1: Некоректні дані
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Редактор|
        start
        : Створює запит на додання даних;
    |Система|
        : Отримує запит;
        : Аналізує введені дані;
        note right #ffaaaa
        <b> Можливо
        <b> EX-1
        end note
        : Додає нові дані;
    |Редактор|
        : Отримує повідомлення о доданні даних;
        stop;

@enduml

### 3.2 Редагування даних

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-1.2
        <font color=000 size=16><b>Назва:</b> Редугавання даних
        <font color=000 size=16><b>Учасники:</b> Редактор, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Редактор, наявні дані
        <font color=000 size=16><b>Результат:</b> Зміна даних
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16>Немає
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Редактор|
        start
        : Створює запит на редагування даних;
    |Система|
        : Отримує запит;
        : Редагує дані;
    |Редактор|
        : Отримує повідомлення о редагуванні даних;
        stop;

@enduml

### 3.3 Архивація даних

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-2
        <font color=000 size=16><b>Назва:</b> Архивація даних
        <font color=000 size=16><b>Учасники:</b> Редактор, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Редактор, наявні дані
        <font color=000 size=16><b>Результат:</b> Архивація даних
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16>Немає
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Редактор|
        start
        : Створює запит на архивацію даних;
    |Система|
        : Отримує запит;
        : Архивує дані;
    |Редактор|
        : Отримує повідомлення об архивації даних;
        stop;

@enduml

### 3.4 Видалення даних

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-3
        <font color=000 size=16><b>Назва:</b> Архивація даних
        <font color=000 size=16><b>Учасники:</b> Редактор, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Редактор, наявні дані
        <font color=000 size=16><b>Результат:</b> Архивація даних
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16>Немає
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Редактор|
        start
        : Створює запит на видалення даних;
    |Система|
        : Отримує запит;
        : Видаляє дані;
    |Редактор|
        : Отримує повідомлення о видаленні даних;
        stop;

@enduml

### 3.5 Додання нового редактора

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-9
        <font color=000 size=16><b>Назва:</b> Додання нового редактора
        <font color=000 size=16><b>Учасники:</b> Редактор, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Редактор, наявність Користувача
        <font color=000 size=16><b>Результат:</b> Новий редактор
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16> EX-2: Користувач не існує
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Редактор|
        start
        : Створює запит на додання нового редактору;
    |Система|
        : Отримує запит;
        : Шукає користувача;
        note right #ffaaaa
        <b> Можливо
        <b> EX-2
        end note
        : Надає права редактора;
    |Редактор|
        : Отримує повідомлення о наданні прав редактору;
        stop
        
@enduml

### 3.6 Пошук даних

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-4
        <font color=000 size=16><b>Назва:</b> Пошук даних
        <font color=000 size=16><b>Учасники:</b> Користувач, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Користувач
        <font color=000 size=16><b>Результат:</b> Відображення даних
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16> EX-3: Дані не існують
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Користувач|
        start
        : Обирає параметри пошуку;
        : Створює запит на пошук даних;
    |Система|
        : Отримує запит;
        : Оброблює запит;
        note right #ffaaaa
        <b> Можливо
        <b> EX-3
        end note
        : Відображує дані;
    |Користувач|
        : Отримує знайдені дані;
        stop
        
@enduml

### 3.7 Відображення даних 

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-5
        <font color=000 size=16><b>Назва:</b> Відображення даних
        <font color=000 size=16><b>Учасники:</b> Користувач, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Користувач, наявні дані
        <font color=000 size=16><b>Результат:</b> Відображення даних графічно
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16> Немає
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Користувач|
        start
        :Обирає дані;
        :Обирає спосіб відображення даних;
        :Надсилає запит на відображення даних;
    |Система|
        :Отримує запит;
        :Оброблює запит;
        :Відображує дані;
    |Користувач|
        :Отримує графічне відображення даних;
        stop
        
@enduml

### 3.8 Завантаження даних

@startuml

    left header
        <font color=000 size=16><b>ID:</b> UC-6
        <font color=000 size=16><b>Назва:</b> Завантаження даних
        <font color=000 size=16><b>Учасники:</b> Користувач, Система
        <font color=000 size=16><b>Передумови:</b> Зареєстрований Користувач, наявні дані
        <font color=000 size=16><b>Результат:</b> Файл даних у користувача
        <font color=000 size=16><b>Виключні ситуації:</b>
        <font color=000 size=16> Немає
        
        <font color=000 size=16><b>Основний сценарій:</b>
    end header

    |Користувач|
        start
        :Обирає дані;
        :Обирає тип завантаження файлу;
        :Надсилає запит на завантаження файлу;
    |Система|
        :Отримує запит; 
        :Підготовлує файл;
        :Надсилає файл;
    |Користувач|
        :Отримує файл даних;
        stop
        
@enduml

