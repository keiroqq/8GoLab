1)	Построение базового REST API:
•	Реализуйте сервер, поддерживающий маршруты:
•	GET /users — получение списка пользователей.
•	GET /users/{id} — получение информации о конкретном пользователе.
•	POST /users — добавление нового пользователя.
•	PUT /users/{id} — обновление информации о пользователе.
•	DELETE /users/{id} — удаление пользователя.
2)	Подключение базы данных:
•	Добавьте базу данных (например, PostgreSQL или MongoDB) для хранения информации о пользователях.
•	Модифицируйте сервер для взаимодействия с базой данных.
3)	Обработка ошибок и валидация данных:
•	Реализуйте централизованную обработку ошибок.
•	Добавьте валидацию данных при создании и обновлении пользователей.
4)	Пагинация и фильтрация:
•	Добавьте поддержку пагинации и фильтрации по параметрам запроса (например, поиск пользователей по имени или возрасту).
5)	Тестирование API:
•	Реализуйте unit-тесты для каждого маршрута.
•	Проверьте корректность работы при различных вводных данных.
6)	Документация API:
•	Создайте документацию для разработанного API с описанием маршрутов, методов, ожидаемых параметров и примеров запросов.

Бд до изменений:
![image](https://github.com/user-attachments/assets/8ea25133-22a3-40f5-8281-d5859fb07cac)

Результат работы GET /users
Вывод всех юзеров:
curl -X GET http://localhost:8000/users:

![image](https://github.com/user-attachments/assets/ccd0a382-88b0-4636-be7a-2d97c16a6395)

Результат работы GET /users/3
Получение инфы по конкретному юзеру:
curl -X GET http://localhost:8000/users/1

![image](https://github.com/user-attachments/assets/826d3839-d9c3-4f00-9272-106b4b8efec4)

Добавление юзера с помощью POST /users
curl -X POST http://localhost:8000/users -H "Content-Type: application/json" -d '{"name": "Trump", "email": "donald@example.com", "age": 46}'

![image](https://github.com/user-attachments/assets/5f7d0fe8-b923-4e74-b1a8-8dc41eb43130)

В нашей бд появился Трамп с id = 9
![image](https://github.com/user-attachments/assets/552d6bfd-c82c-4a38-b41d-1cdb552ed6ec)

Обновление инфы о юзере с помощью PUT /users/{id}
curl -X PUT http://localhost:8000/users/9 -H "Content-Type: application/json" -d '{"name": "Osanov VA", "email": "coolstorybob@example.com", "age": 25}'
Изменим по id = 9 данные:

![image](https://github.com/user-attachments/assets/8e118097-77fd-42f2-af8a-ed6e9ab0f27a)

![image](https://github.com/user-attachments/assets/6156d0e4-42b5-4240-abbd-cc06b5aa925f)

Удалим пользователя с id = 9 с помощью DELETE /users/{id}
curl -X DELETE http://localhost:8000/users/9

![image](https://github.com/user-attachments/assets/aa675906-518e-4fbc-abf6-f3b189b30c2f)

До:

![image](https://github.com/user-attachments/assets/dabed905-c8c0-4510-8857-18ec7ae1f4b4)

После:

![image](https://github.com/user-attachments/assets/f79d6d7c-f03c-4fa5-bdeb-3272be9ab760)

Проверка на валидацию
Если мы укажем неверный формат email или некорректный возраст (>120), то функция вернет ошибку валидации.
К примеру, укажем некорректный email:

![image](https://github.com/user-attachments/assets/dacc715c-7769-4cb8-a56f-c62e14cb4c90)


