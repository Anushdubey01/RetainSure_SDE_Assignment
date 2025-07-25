# CHANGES.md

## Major Issues Identified
- SQL injection vulnerabilities due to string interpolation in SQL queries
- Plaintext password storage and comparison
- No input validation or error handling
- All logic in a single file, no separation of concerns
- Inconsistent API responses and HTTP status codes

## Changes Made
- Refactored codebase into modular structure: separate files for database logic, models, and routes (using Flask Blueprints)
- All SQL queries now use parameterized queries to prevent SQL injection
- Passwords are hashed using Werkzeug's `generate_password_hash` and checked with `check_password_hash`
- Input validation added for user creation and login (email format, password length)
- Consistent JSON API responses and proper HTTP status codes
- Database connection logic moved to `db.py` with Flask context management
- Sample data in `init_db.py` now uses hashed passwords

## Architectural Decisions
- Used Flask Blueprints for route organization to improve maintainability
- Kept models as simple functions for this small app, but could be expanded to classes for larger projects
- Used Werkzeug for password security as it is standard with Flask

## Trade-offs and Assumptions
- Did not implement advanced validation or error handling for all endpoints (can be added if needed)
- Did not add user registration confirmation or email uniqueness checks (out of scope per requirements)
- Kept the database as SQLite for simplicity

## With More Time
- Add more comprehensive input validation and error handling
- Implement user registration confirmation and email uniqueness
- Add automated tests for all endpoints
- Use environment variables for configuration (e.g., DB path, secret keys)
- Add logging and monitoring

## AI Usage
- Used AI (ChatGPT) for code refactoring, security improvements, and documentation drafting
- All code was reviewed and adapted for the assignment requirements 