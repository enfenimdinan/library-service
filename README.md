# Library Service
A library management application built for learning purposes on Java.

## MVP capabilities
The first version focuses on six core capabilities:

1. Books
2. Physical book copies
3. Members
4. Borrowing
5. Returning
6. Overdue-loan view

## Core logic
Initial scope for the MVP:
1. A physical copy can have only one active loan at a time.
2. A loan lasts 14 days.
3. A member can have at most five active loans.
4. A book and a physical copy are different concepts: one book can have multiple copies.
5. A copy cannot be borrowed when it is already on loan.
6. A due date is calculated by the server, not supplied by the client.
7. Loan history is preserved after a book is returned.
8. Invalid or impossible state changes produce explicit errors instead of silently changing data.
9. The backend enforces authorization rules.


## Users’ types
**Member**
- browse and search the catalog
- view book availability
- view their loans
- borrow and return books through supported flows
- see overdue loans

**Librarian**
- manage catalog data
- manage members
- administer borrowing and returns
- inspect loan status

## Tech
### Backend
- Java
- Spring Boot
- Spring Web
- Spring Data JPA
- PostgreSQL
- Flyway
- Spring Security
- Maven
- Testcontainers
- JUnit
- Docker
- OpenAPI

## Architecture
The backend is a modular monolith.
    
Planned high-level structure:

```text
catalog
├── domain
├── application
└── adapter
    ├── in.web
    └── out.persistence

loans
├── domain
├── application
└── adapter
    ├── in.web
    └── out.persistence

shared
```

Typical request flow:

```text
HTTP request
    ↓
Controller
    ↓
Application use case
    ↓
Domain rules
    ↓
Repository contract
    ↓
Persistence adapter
    ↓
PostgreSQL
```

The domain should not depend on HTTP controllers or JPA details.
