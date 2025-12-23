# Практическая работа 4
Голубев Илья ЭФМО-02-25
# Описание проекта
Маршрутизация с chi, Создание небольшого CRUD-сервиса
Цели:	
- Освоить базовую маршрутизацию HTTP-запросов в Go на примере роутера chi.
- Научиться строить REST-маршруты и обрабатывать методы GET/POST/PUT/DELETE.
- Реализовать небольшой CRUD-сервис «ToDo» (без БД, хранение в памяти).
- Добавить простое middleware (логирование, CORS).
- Научиться тестировать API запросами через curl/Postman/HTTPie.
# Требования
Go версии 1.21 и выше и Git
# Установка и запуск
Клонировать репозиторий:
```
git clone https://github.com/iliaglbv/PR4
cd PR4
```
Команда запуска сервера:
```
go run .
```
# Структура проекта
```plaintext
PR4/                                                
├── internal/              
│   └── task/               
│   │   └── handler.go     
│   │   └── model.go  
│   │   └── repo.go
├── pkg/
│   └── middleware/
│        └──cors.go
│        └──logger.go       
├── go.mod
├── go.sum                
└── main.go    
```
# Основные эндпоинты и их проверка
Проверка работы сервера
        
    curl  0.0.0.0:8080/health
<img width="500" height="309" alt="Gethealtht_1" src="https://github.com/user-attachments/assets/759b2548-d142-4943-94b4-494dd2c98f5d" />

Создание задачи

    curl -X POST http://localhost:8080/api/tasks ^
    -H "Content-Type: application/json" ^
    -d "{\"title\":\"Выучить chi\"}"

<img width="497" height="400" alt="Post1" src="https://github.com/user-attachments/assets/dfee593a-340e-497c-9683-451734d2fc7b" />

Получение списка задач

    curl http://localhost:8080/api/tasks

  <img width="591" height="501" alt="GEttasks_1" src="https://github.com/user-attachments/assets/8c838e60-5c1e-4b94-96e9-c63e4428483b" />
  
Получение задачи по id

    curl http://localhost:8080/api/tasks/1

  <img width="587" height="403" alt="id_1" src="https://github.com/user-attachments/assets/b2c74c34-d63d-4266-b087-bccf280d8651" />
  
Обновление задачи

    curl -X PUT http://localhost:8080/api/tasks/2 ^
    -H "Content-Type: application/json" ^
    -d "{\"title\":\"Выучить chi глубже\",\"done\":true}"
<img width="579" height="398" alt="redot_1" src="https://github.com/user-attachments/assets/8470efdc-c074-43f0-9e04-5344e24b0852" />

Удаление задачи

    curl -X DELETE http://localhost:8080/api/tasks/1
<img width="588" height="344" alt="delete_1" src="https://github.com/user-attachments/assets/e201cf34-91c3-463b-9ccb-5f0231555e31" />

Проверка списка после удаления

<img width="579" height="496" alt="Check_1" src="https://github.com/user-attachments/assets/b29679d3-a966-4cb3-9ab2-9a0d3af49587" />

# Запуск и логи проекта

<img width="355" height="174" alt="logt_1" src="https://github.com/user-attachments/assets/213cdb3d-55d0-4542-b076-52cff042914d" />

