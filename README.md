# ERP Data Models Repository

## Purpose

This repository contains SQL data models and stored procedures for an Enterprise Resource Planning (ERP) system. The SQL files are designed to work with SQL Server 2019 and provide standardized database operations for managing employees, orders, products, and warehouse shelves.

## Repository Structure

```
data-models/
├── employees/              # Employee management operations
│   ├── create_employee.sql                  # Creates new employee records (SSO setup/automation)
│   ├── update_employee.sql                  # Updates existing employee information
│   └── disable_employee.sql                 # Disables employee accounts
│
├── orders/                 # Order management operations
│   ├── get_order_info.sql                   # Retrieves order details (includes comments, events, etc.)
│   ├── update_order_logistics_state.sql     # Updates order state (picking, packing, etc.)
│   ├── append_order_event.sql               # Adds events to order history
│   ├── view_pickable_orders_products.sql    # Lists pickable products on orders
│   └── view_processing_backordered_order_products.sql  # Shows backordered items
│
├── products/               # Product management operations
│   ├── get_product_info.sql                 # Retrieves product details
│   ├── append_product_log.sql               # Logs product-related events
│   └── update_product_shelf.sql             # Updates product shelf assignments
│
└── shelves/                # Warehouse shelf management
    ├── view_shelf_info_all.sql              # Lists all shelves with metadata
    ├── append_shelf_log.sql                 # Logs shelf-related actions
    └── get_shelf_info_single.sql            # Retrieves single shelf details
```

## Usage

Each SQL file contains a stored procedure or view designed for specific operations within the ERP system. To use these files:

1. **Connect to your SQL Server 2019 instance**
2. **Execute the SQL files** in the appropriate database context
3. **Call the procedures** with the required parameters as documented in each file

### Example Usage

```sql
-- Create a new employee
EXEC create_employee 
    @EmployeeID = 'EMP001',
    @FirstName = 'John',
    @LastName = 'Doe',
    @Email = 'john.doe@company.com';

-- Get order information
EXEC get_order_info @OrderID = 'ORD12345';

-- Update product shelf location
EXEC update_product_shelf 
    @ProductID = 'PROD001',
    @ShelfID = 'SHELF-A1';
```

## SQL Server 2019 Compatibility Notes

- All procedures use SQL Server 2019 syntax and features
- Temporal tables may be used for audit trails
- JSON support is available for complex data structures
- Row-level security can be implemented where needed
- Always use parameterized queries to prevent SQL injection

## Best Practices

1. **Always use transactions** for operations that modify multiple tables
2. **Include error handling** with TRY-CATCH blocks
3. **Log all critical operations** to audit tables
4. **Use appropriate indexes** for frequently queried columns
5. **Follow naming conventions** consistently across all procedures

## Contributing

When adding new SQL files:
- Place them in the appropriate folder based on the entity they manage
- Include comprehensive comments explaining purpose and usage
- Add parameter validation and error handling
- Update this README with the new file description

## Version Control

This repository uses Git for version control. All database schema changes should be:
- Committed with descriptive messages
- Tagged with version numbers for releases
- Reviewed before merging to main branch