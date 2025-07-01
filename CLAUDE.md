# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a SQL Server 2019 data models repository containing stored procedures and SQL scripts for an Enterprise Resource Planning (ERP) system. The repository manages database operations for employees, orders, products, and warehouse shelves.

## Database Architecture

The ERP system is organized into four main entity domains:

- **employees/**: Employee management operations (creation, updates, deactivation)
- **orders/**: Order lifecycle management (retrieval, logistics state updates, event logging, pickable/backordered views)
- **products/**: Product data management (information retrieval, shelf assignments, activity logging)
- **shelves/**: Warehouse shelf operations (information retrieval, activity logging)

Each domain contains SQL files that implement specific stored procedures or views for database operations.

## Development Practices

### SQL Standards
- All SQL scripts target SQL Server 2019 compatibility
- Use parameterized queries to prevent SQL injection
- Include comprehensive error handling with TRY-CATCH blocks
- Implement transaction management for multi-table operations
- Add audit logging for critical operations

### File Organization
- Place new SQL files in the appropriate domain folder based on the entity they manage
- Use descriptive filenames that indicate the operation (e.g., `get_order_info.sql`, `update_product_shelf.sql`)
- Include comprehensive comments explaining purpose, parameters, and usage

### Testing and Deployment
- Test all procedures against SQL Server 2019 instance before committing
- Validate parameter inputs and include appropriate error messages
- Document any dependencies on existing tables or procedures
- Update README.md when adding new files

## Common Operations

Since this is a pure SQL repository with no build system:
- No build, test, or lint commands are available
- Direct SQL Server execution is required for testing
- Version control through Git provides change tracking
- Manual deployment to target database instances

## SQL File Patterns

Most SQL files follow these patterns:
- Single-purpose stored procedures or views
- Parameterized inputs where applicable
- Simple operations like SELECT, UPDATE, INSERT statements
- Example: `disable_employee.sql` contains: `UPDATE tblUsers SET Active = 0 WHERE UserID = @UserID;`

When working with this repository, focus on SQL Server 2019 compatibility and maintaining the established organizational structure by entity domain.