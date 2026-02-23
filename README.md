# EF Core Training: By Convention & Data Annotation

## Overview
This repository contains a training project demonstrating how to use **Entity Framework Core (EF Core)** for database modeling using **By Convention** and **Data Annotations**. The project includes two separate DbContexts:

1. **ITI_DbContext**: Represents an educational system.
2. **AirLineDbContext**: Represents an airline management system.

The training focuses on creating entities, defining relationships, and applying EF Core conventions and Data Annotations to manage the database schema.

---

## Project Structure

- **ITI_Classes**
  - **DataBaseContext**
    - `ITI_DbContext.cs`
  - **Entities**
    - `Courses`, `Topics`, `Students`, `Instructors`, `Departments`, `Stud_Course`, `Course_Instructor`

- **AirLine_Classes**
  - **DataBaseContext**
    - `AirLineDbContext.cs`
  - **Entities**
    - `AirLine`, `AirCraft`, `Route`, `Aircraft_Routes`, `Employee`, `Emp_Qualifications`, `Transaction`, `AirLine_Phones`

---

## ITI_DbContext

**Entities and Relationships:**

- `Courses`
- `Topics`
- `Students`
- `Instructors`
- `Departments`
- `Stud_Course` (Many-to-Many between Students and Courses)
- `Course_Instructor` (Many-to-Many between Courses and Instructors)

**Key Points:**

- Relationships are handled using **By Convention** whenever possible.
- **Composite keys** are defined for many-to-many linking tables using `OnModelCreating`.
- Properties are automatically mapped to columns based on naming conventions.

---

## AirLineDbContext

**Entities and Relationships:**

- `AirLine`
- `AirCraft`
- `Route`
- `Aircraft_Routes` (Many-to-Many between AirCraft and Route)
- `Employee`
- `Emp_Qualifications`
- `Transaction`
- `AirLine_Phones`

**Key Points:**

- By Convention mapping is applied for simple entities.
- Navigation properties establish relationships between entities.
- Composite keys or special constraints are defined using Fluent API in `OnModelCreating`.
- Demonstrates handling multiple DbContexts in the same solution.

---

## EF Core Concepts Covered

1. **By Convention Mapping**
   - EF Core automatically maps properties to columns and classes to tables based on naming conventions.
   - Navigation properties automatically infer foreign keys.

2. **Data Annotation Mapping**
   - Attributes like `[Key]`, `[Required]`, `[MaxLength]`, `[ForeignKey]` are used to explicitly define schema rules.

3. **DbContext Setup**
   - Each context contains a `DbSet<TEntity>` for each entity.
   - Connection strings are configured in `OnConfiguring()`.

4. **Migrations**
   - Adding migrations with `Add-Migration` command.
   - Applying migrations to create or update the database using `Update-Database`.

---

# EF Core Training: Usage Instructions & Notes

## Usage Instructions
Open the project in Visual Studio. Restore NuGet packages using `Update-Package`. Add a migration (example for AirLineDbContext) using `Add-Migration -Name "AirLineMigration" -Context "AirLineDbContext" -OutputDir "AirLineMigrations"`. Apply the migration to the database using `Update-Database -Context AirLineDbContext`. Repeat similar steps for ITI_DbContext if needed.

## Notes
Ensure the connection strings in `OnConfiguring()` are valid for your SQL Server instance. Composite keys were defined in `OnModelCreating` for many-to-many relationships. This project demonstrates EF Core best practices and can be extended for real-world applications.



