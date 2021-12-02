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

    User -u-> UC_4
    User -u-> UC_5
    User -u-> UC_6
    
    Editor -u-|> User
    
    Editor -u-> UC_1
    Editor -u-> UC_2
    Editor -u-> UC_3
    UC_1.1 .u.> UC_1: extends
    UC_1.2 .u.> UC_1: extends

    
@enduml

## Модель використання користувача

@startuml
    actor "Користувач" as User
    
  
    usecase "<b>UC_4</b>\nПошук даних" as UC_4
    usecase "<b>UC_5</b>\nВідображення даних" as UC_5
    usecase "<b>UC_6</b>\nЗавантаження даних" as UC_6


    User -u-> UC_4
    User -u-> UC_5
    User -u-> UC_6

    
@enduml

## Модель використання редактора

@startuml
    
    actor "Редактор" as Editor
    
    usecase "<b>UC_1</b>\nCупроводження даних" as UC_1
    usecase "<b>UC_2</b>\nАрхівація даних" as UC_2
    usecase "<b>UC_3</b>\nВидалення даних" as UC_3
    usecase "<b>UC_1.1</b>\nДодання даних" as UC_1.1
    usecase "<b>UC_1.2</b>\nРедагування даних" as UC_1.2

    
    Editor -u-> UC_1
    Editor -u-> UC_2
    Editor -u-> UC_3
    UC_1.1 .u.> UC_1: extends
    UC_1.2 .u.> UC_1: extends

    
@enduml

# Сценарії 