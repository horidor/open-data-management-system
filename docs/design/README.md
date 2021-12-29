# Проєктування бази даних

- ER-модель

@startuml

package "DataSets" {
entity DataPoints <<ENTITY>> {
    id:INT 
    key: INT
    value:VARCHAR
}

entity Entities <<ENTITY>> {
    id: INT
    entity: VARCHAR
    property: VARCHAR
}

entity Concepts <<ENTITY>> {
    id INT
    concept: VARCHAR
    concept_type: VARCHAR
    drill_up: VARCHAR
    domain: VARCHAR
}

entity MetaData <<ENTITY>> {
    id: INT
    key: INT
    value: VARCHAR
}

entity Synonyms <<ENTITY>> {
    id: INT
    mainWord: INT
    synonym: INT
    value: VARCHAR
}      
}

entity Users <<ENTITY>> {
	id:INT
	username:VARCHAR
	email:VARCHAR
	password:VARCHAR
	role:VARCHAR
}

entity FileAccess <<ENTITY>> {

}

entity Files <<Entity>> {
    id: INT
    fileName: VARCHAR
    filepath: VARCHAR
    uploaded: DATE
    
}

entity FilesArchived <<Entity>> { 
    id: INT
    fileName: VARCHAR
    filepath: VARCHAR
    uploaded: DATE
    archived: DATE
}

entity UserAccess <<Entity>>{

}


DataPoints "1,1" -- "1,1" Concepts
DataPoints "1,1" -l- "1,1" Entities
MetaData "0,1" -r- "1,1" DataPoints
Entities "1,1" -- "1,1" Concepts
MetaData "0,1" -- "1,1" Concepts
Synonyms "0,1" -r- "1,1" Concepts
Synonyms "0,1" -l- "1,1" Entities
MetaData "0,1" -- "1,1" Entities

"DataSets" "1,*" .u. "1,1" FileAccess
FileAccess "0,*" .r. "1,1" Files
FileAccess "0,*" .u. "1,1" FilesArchived

Files "1, 1" .r. "0, *" UserAccess
FilesArchived "1, 1" .r. "0, *" UserAccess

UserAccess "0,*" -r- "1,1" Users

@enduml