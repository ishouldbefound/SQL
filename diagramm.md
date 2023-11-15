## диаграмма
![awwawa](https://github.com/ishouldbefound/SQL/assets/144837901/e5d247ce-c488-4d32-b02b-059dda6f6c81)
## Создание таблиц
Countries:
```sql
CREATE TABLE Countries (
  id INT PRIMARY KEY,
  Country VARCHAR(255) NOT NULL
);
```

Guests:
```sql
CREATE TABLE Guests (
  id INT PRIMARY KEY,
  Firstname VARCHAR(255) NOT NULL,
  Surname VARCHAR(255) NOT NULL,
  Phone_number VARCHAR(15),
  email VARCHAR(255),
  Birthday DATE,
  Sex VARCHAR(10),
  Country_id INT,
  FOREIGN KEY (Country_id) REFERENCES Countries(id)
);
```

Services:
```sql
CREATE TABLE Services (
  id INT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  description TEXT,
  price FLOAT NOT NULL,
  Phone_number VARCHAR(15)
);
```

Services_orders: 
```sql
CREATE TABLE Services_orders (
  id INT PRIMARY KEY,
  price FLOAT NOT NULL,
	service_id INT NOT NULL,
	guest_id INT NOT NULL,
	FOREIGN KEY (service_id) REFERENCES Services(id),
  FOREIGN KEY (guest_id) REFERENCES Guests(id)
);
```

Payments:
```sql
CREATE TABLE Payments (
  id INT PRIMARY KEY,
	guest_id INT NOT NULL,
  description VARCHAR(255) NOT NULL,
  order_date DATE NOT NULL,
  price FLOAT NOT NULL,
  FOREIGN KEY (guest_id) REFERENCES Guests(id)
);
```

Room_types:
```sql
CREATE TABLE Room_types (
  id INT PRIMARY KEY,
  type VARCHAR(255),
  description VARCHAR(255)
);
```

Statuses:
```sql
CREATE TABLE Statuses (
  id INT PRIMARY KEY,
  status VARCHAR(255)
);
```

Rooms:
```sql
CREATE TABLE Rooms (
  id INT PRIMARY KEY,
  type_id INT NOT NULL,
  status_id INT NOT NULL,
  price FLOAT NOT NULL,
  FOREIGN KEY (type_id) REFERENCES Room_types(id),
  FOREIGN KEY (status_id) REFERENCES Statuses(id)
);
```

Bonuses:
```sql
CREATE TABLE Bonuses (
  id INT PRIMARY KEY,
  description VARCHAR(255) NOT NULL
);
```

Guest_loyalty:
```sql
CREATE TABLE Guest_loyalty (
  id INT PRIMARY KEY,
  guest_id INT,
  status_id INT,
  bonus_id INT,
  FOREIGN KEY (guest_id) REFERENCES Guests(id),
  FOREIGN KEY (status_id) REFERENCES Statuses(id),
  FOREIGN KEY (bonus_id) REFERENCES Bonuses(id)
);
```

Review:
```sql
CREATE TABLE Review (
  id INT PRIMARY KEY,
  guest_id INT,
  service_id INT,
  rating INT,
  comment VARCHAR(255),
  FOREIGN KEY (guest_id) REFERENCES Guests(id),
  FOREIGN KEY (service_id) REFERENCES Services(id)
);
```

Bookings:
```sql
CREATE TABLE Bookings (
  id INT PRIMARY KEY,
  guest_id INT,
  room_id INT,
  arrival_date DATE,
  departure_date DATE,
  FOREIGN KEY (guest_id) REFERENCES Guests(id),
  FOREIGN KEY (room_id) REFERENCES Rooms(id)
);
```

Departments: 
```sql
CREATE TABLE Departments (
  id INT PRIMARY KEY,
  title VARCHAR(255),
  description TEXT
);
```

Staff_positions:
```sql
CREATE TABLE Staff_positions (
  id INT PRIMARY KEY,
  position VARCHAR(255),
  description TEXT
);
```

Staff:
```sql
CREATE TABLE Staff (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  surname VARCHAR(255),
  position_id INT,
  phone_number VARCHAR(20),
  FOREIGN KEY (position_id) REFERENCES Staff_positions(id)
);
```

Staff_departments:
```sql
CREATE TABLE Staff_departments (
  id INT PRIMARY KEY,
  department_id INT,
  staff_id INT,
  FOREIGN KEY (staff_id) REFERENCES Staff(id)
);
```

## code for me
```sql
CREATE TABLE Countries (
  id INT PRIMARY KEY,
  Country VARCHAR(255) NOT NULL
);

CREATE TABLE Guests (
  id INT PRIMARY KEY,
  Firstname VARCHAR(255) NOT NULL,
  Surname VARCHAR(255) NOT NULL,
  Phone_number VARCHAR(15),
  email VARCHAR(255),
  Birthday DATE,
  Sex VARCHAR(10),
  Country_id INT,
  FOREIGN KEY (Country_id) REFERENCES Countries(id)
);

CREATE TABLE Services (
  id INT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  description TEXT,
  price FLOAT NOT NULL,
  Phone_number VARCHAR(15)
);

CREATE TABLE Services_orders (
  id INT PRIMARY KEY,
  price FLOAT NOT NULL,
	service_id INT NOT NULL,
	guest_id INT NOT NULL,
	FOREIGN KEY (service_id) REFERENCES Services(id),
  FOREIGN KEY (guest_id) REFERENCES Guests(id)
);

CREATE TABLE Payments (
  id INT PRIMARY KEY,
	guest_id INT NOT NULL,
  description VARCHAR(255) NOT NULL,
  order_date DATE NOT NULL,
  price FLOAT NOT NULL,
  FOREIGN KEY (guest_id) REFERENCES Guests(id)
);

CREATE TABLE Room_types (
  id INT PRIMARY KEY,
  type VARCHAR(255),
  description VARCHAR(255)
);

CREATE TABLE Statuses (
  id INT PRIMARY KEY,
  status VARCHAR(255)
);

CREATE TABLE Rooms (
  id INT PRIMARY KEY,
  type_id INT NOT NULL,
  status_id INT NOT NULL,
  price FLOAT NOT NULL,
  FOREIGN KEY (type_id) REFERENCES Room_types(id),
  FOREIGN KEY (status_id) REFERENCES Statuses(id)
);

CREATE TABLE Bonuses (
  id INT PRIMARY KEY,
  description VARCHAR(255) NOT NULL
);

CREATE TABLE Guest_loyalty (
  id INT PRIMARY KEY,
  guest_id INT,
  status_id INT,
  bonus_id INT,
  FOREIGN KEY (guest_id) REFERENCES Guests(id),
  FOREIGN KEY (status_id) REFERENCES Statuses(id),
  FOREIGN KEY (bonus_id) REFERENCES Bonuses(id)
);

CREATE TABLE Review (
  id INT PRIMARY KEY,
  guest_id INT,
  service_id INT,
  rating INT,
  comment VARCHAR(255),
  FOREIGN KEY (guest_id) REFERENCES Guests(id),
  FOREIGN KEY (service_id) REFERENCES Services(id)
);

CREATE TABLE Bookings (
  id INT PRIMARY KEY,
  guest_id INT,
  room_id INT,
  arrival_date DATE,
  departure_date DATE,
  FOREIGN KEY (guest_id) REFERENCES Guests(id),
  FOREIGN KEY (room_id) REFERENCES Rooms(id)
);

CREATE TABLE Departments (
  id INT PRIMARY KEY,
  title VARCHAR(255),
  description TEXT
);

CREATE TABLE Staff_positions (
  id INT PRIMARY KEY,
  position VARCHAR(255),
  description TEXT
);

CREATE TABLE Staff (
  id INT PRIMARY KEY,
  name VARCHAR(255),
  surname VARCHAR(255),
  position_id INT,
  phone_number VARCHAR(20),
  FOREIGN KEY (position_id) REFERENCES Staff_positions(id)
);

CREATE TABLE Staff_departments (
  id INT PRIMARY KEY,
  department_id INT,
  staff_id INT,
  FOREIGN KEY (staff_id) REFERENCES Staff(id)
);
```

Внесение записей в таблицу:
```sql
INSERT INTO Countries (id, Country) VALUES
  (1, 'США'),
  (2, 'Канада'),
  (3, 'Бразилия'),
  (4, 'Франция'),
  (5, 'Германия'),
  (6, 'Индия'),
  (7, 'Китай'),
  (8, 'Япония'),
  (9, 'Австралия'),
  (10, 'Мексика'),
  (11, 'Аргентина'),
  (12, 'Россия'),
  (13, 'Южная Африка'),
  (14, 'Италия'),
  (15, 'Испания'),
  (16, 'Великобритания'),
  (17, 'Нидерланды'),
  (18, 'Швейцария'),
  (19, 'Швеция'),
  (20, 'Норвегия'),
  (21, 'Новая Зеландия'),
  (22, 'Южная Корея'),
  (23, 'Сингапур'),
  (24, 'Таиланд'),
  (25, 'Египет'),
  (26, 'Нигерия'),
  (27, 'Саудовская Аравия'),
  (28, 'Турция'),
  (29, 'Вьетнам'),
  (30, 'Чили');
```
