# 1. Naming of Items Entities

Date: 2024-03-21

## Status

Accepted

## Labels
items

## Context

As we develop the items service, we need consistent naming conventions for item entities to:
- Maintain code readability and clarity
- Ensure consistent domain language across the codebase
- Avoid confusion between similar concepts
- Make the code self-documenting

## Decision

We will adopt the following naming conventions for item entities:

1. Core Item Entities:
   - `Item` - The base item record
   - `ItemVariant` - Variations of an item (size, color, etc.)
   - `ItemCategory` - Classification grouping for items
   - `ItemAttribute` - Configurable properties of items

2. Supporting Entities:
   - `ItemInventory` - Stock levels and locations
   - `ItemPrice` - Pricing information and history
   - `ItemSupplier` - Vendor/manufacturer details

3. Prefix Rules:
   - Use `Item` prefix for primary domain entities
   - Omit prefix for generic supporting entities (e.g., `Category`, `Supplier`)

## Consequences

### Positive
- Clear distinction between item and non-item entities
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