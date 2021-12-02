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
@startuml

left header
    <font color=000 size=16><b>ID:</b> UC-1
    <font color=000 size=16><b>Назва:</b> Авторизуватися у системі
    <font color=000 size=16><b>Учасники:</b> Користувач, Система
    <font color=000 size=16><b>Передумови:</b> Зареєстрований користувач
    <font color=000 size=16><b>Результат:</b> Доступ до системи
    <font color=000 size=16><b>Виключні ситуації:</b>
    <font color=000 size=16>EX-1: Не вірний логін/пароль
    
    <font color=000 size=16><b>Основний сценарій:</b>
end header

|Користувач|
    start
    : Натискає на кнопку "Login";
|Система|
    : Пропонує форму "Login";
|Користувач|
    : Заповнює поля: "Username", "Password";
    : Відсилає заповнену форму;
|Система|
    : Перевіряє введені дані;
    note right #ffaaaa
    <b> Можливо
    <b> EX-1
    end note
    : Надає доступ до сайту;
|Користувач|
    stop;
@enduml
