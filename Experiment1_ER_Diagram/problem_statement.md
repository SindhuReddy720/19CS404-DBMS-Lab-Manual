# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="1536" height="1024" alt="272460eb-3678-4b57-814d-434b157cbb81" src="https://github.com/user-attachments/assets/6eb2f9b1-d5bb-484e-baed-8f1f652b90f7" />


### Entities and Attributes

<img width="855" height="167" alt="Screenshot 2026-08-20 214726" src="https://github.com/user-attachments/assets/0dfdb0de-bbb1-4aa9-a309-64edd75bc49d" />


### Relationships and Constraints

<img width="1007" height="165" alt="Screenshot 2026-08-20 215338" src="https://github.com/user-attachments/assets/ac873ba1-f227-4abf-bfc1-6b3904799620" />


### Assumptions
- A member can enroll in more than one fitness program, such as Yoga, Zumba, or Weight Training.
- A fitness program can have multiple trainers assigned to it.
- Personal training sessions are conducted by trainers, attendance is recorded, and payments are tracked for memberships and sessions.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:

<img width="1536" height="1024" alt="60c387e5-4c46-471f-b6d0-af1df9485417" src="https://github.com/user-attachments/assets/917f72fd-2965-4c60-8f58-30d52823d9f6" />


### Entities and Attributes

<img width="460" height="206" alt="Screenshot 2026-08-20 220836" src="https://github.com/user-attachments/assets/d2d3d75e-125f-49ce-b50e-bcddf514275a" />


### Relationships and Constraints

<img width="501" height="208" alt="Screenshot 2026-08-20 220856" src="https://github.com/user-attachments/assets/aaf16736-5e01-4e9d-ad5d-47f03a1df6c4" />

### Assumptions
- A member can borrow multiple books, and a book can be borrowed by multiple members over time.
- A separate loan record is maintained for each book borrowed, with loan date and return date.
- A member can register for multiple events, and an event can have multiple members.
- Each event can have one or more speakers/authors.
- Each event is booked in one room, while a room can be used for multiple events.
- Overdue fines are calculated based on the return date of the borrowed book. 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

<img width="1397" height="1126" alt="3e6a8e9a-8c47-440e-8258-719cd09f4cc4" src="https://github.com/user-attachments/assets/7814ac99-867d-4b22-99f7-6ae9819d1394" />


### Entities and Attributes

<img width="1010" height="300" alt="image" src="https://github.com/user-attachments/assets/70f9b806-80db-4260-938c-9150b2b98612" />


### Relationships and Constraints

<img width="1046" height="272" alt="Screenshot 2026-08-20 222505" src="https://github.com/user-attachments/assets/e7883d03-1e5e-4374-8cd6-d8add81ce2ae" />


### Assumptions
- A customer can make multiple reservations and place multiple orders.
- Each reservation is associated with a table and waiter.
- A bill is generated for each reservation.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
