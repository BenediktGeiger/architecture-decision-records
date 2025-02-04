# 1. Naming of Sales Entities

Date: 2024-03-21

## Status

Accepted

## Context

As we develop the sales service, we need consistent naming conventions for sales entities to:
- Maintain code readability and clarity
- Ensure consistent domain language across the codebase
- Avoid confusion between similar concepts
- Make the code self-documenting

## Decision

We will adopt the following naming conventions for sales entities:

1. Core Sales Entities:
   - `SalesOrder` - The main transaction record
   - `SalesOrderItem` - Individual line items within an order
   - `SalesQuote` - Pre-order price estimates
   - `SalesContract` - Formal agreement documents

2. Supporting Entities:
   - `SalesTerritory` - Geographic sales regions
   - `SalesTarget` - Revenue/performance goals
   - `SalesCommission` - Commission calculations

3. Prefix Rules:
   - Use `Sales` prefix for primary domain entities
   - Omit prefix for generic supporting entities (e.g., `Customer`, `Product`)

## Consequences

### Positive
- Clear distinction between sales and non-sales entities
- Consistent terminology across codebase
- Improved code navigation and searchability
- Better alignment with domain language

### Negative
- Slightly longer class names
- Need to update existing code to match convention

### Mitigations
- Create automated rename scripts
- Document naming patterns in team wiki
- Review existing code in planned sprints