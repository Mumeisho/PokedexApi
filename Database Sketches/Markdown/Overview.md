# Pokemon Database Schema - Overview & Relationships

## Core Relationship Flow

```md
Pokemon (Species) 
    ↓
Pokemon_Forms (Base, Regional, Alternate, Shiny)
    ↓  
Pokemon_Form_Games (Game-specific stats, availability)
    ↓
Types, Abilities, Locations, Moves (Associated data)
```

## Key Design Principles

### 1. **Separation of Concerns**

- **Universal data** (species name, dex number) stays at Pokemon level
- **Form-specific data** (appearance, some stats) at Form level  
- **Game-specific data** (availability, locations, exact stats) at Form-Game level

### 2. **Flexibility for Edge Cases**

- **Alcremie forms**: Same stats/types, different sprites → Form level handles visuals
- **Ogerpon masks**: Different types per form → Form-Game level handles type differences
- **Regional variants**: Different stats/types → Separate forms with game-specific data
- **Mega evolutions**: Battle-only forms with dramatically different stats

### 3. **Historical Data**

- Same Pokemon can have different stats across generations
- Moves, abilities, and availability change between games
- Type effectiveness changes (Steel/Dark added in Gen 2, Fairy in Gen 6)

## Data Integrity Constraints

### Business Rules to Enforce

- Every Pokemon must have at least one "base" form where `is_default = true`
- Shiny forms should reference the same base stats as their non-shiny counterpart
- Evolution chains must be acyclic (no Pokemon evolves into itself)
- Type effectiveness factors must be valid multipliers (0, 0.25, 0.5, 1, 2, 4)
- Encounter chances in the same location/method should sum to reasonable totals
