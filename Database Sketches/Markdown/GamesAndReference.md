# Pokemon Database Schema - Games & Reference Data

## Games

### **All Pokemon games and versions**

- `game_id` (Primary Key)
- `game_name` (e.g., "Red", "Blue", "Sword", "Violet")
- `game_identifier` (e.g., "red", "blue", "sword", "violet")
- `generation` (Integer - 1-9)
- `version_group_id` (Foreign Key → version_groups)
- `release_date` (Date)
- `platform` (e.g., "Game Boy", "Nintendo Switch")
- `is_main_series` (Boolean)

## Version Groups

### **Games that share the same data (e.g., Red/Blue, Diamond/Pearl)**

- `version_group_id` (Primary Key)
- `version_group_name` (e.g., "Red/Blue", "Diamond/Pearl", "Sword/Shield")
- `version_group_identifier` (e.g., "red-blue", "diamond-pearl")
- `generation` (Integer)

## Types

### **Pokemon types (Fire, Water, etc.)**

- `type_id` (Primary Key)
- `type_name` (e.g., "Fire", "Water", "Electric")
- `type_identifier` (e.g., "fire", "water", "electric")
- `generation_introduced` (Integer)
- `damage_class` (Enum: "physical", "special", "status" - for moves)

## Type Effectiveness

### **Type matchup chart**

- `attacking_type_id` (Foreign Key → types)
- `defending_type_id` (Foreign Key → types)
- `damage_factor` (Float - 0.0, 0.25, 0.5, 1.0, 2.0, 4.0)

## Abilities

### **Pokemon abilities**

- `ability_id` (Primary Key)
- `ability_name` (e.g., "Overgrow", "Blaze", "Static")
- `ability_identifier` (e.g., "overgrow", "blaze", "static")
- `generation_introduced` (Integer)
- `is_main_series` (Boolean)

## Ability Descriptions

### **Game-specific ability descriptions**

- `ability_id` (Foreign Key → abilities)
- `version_group_id` (Foreign Key → version_groups)
- `flavor_text` (Text)
- `short_effect` (Text - brief mechanical description)
- `effect` (Text - detailed mechanical description)

## Growth Rates

### **Experience curves for leveling**

- `growth_rate_id` (Primary Key)
- `growth_rate_name` (e.g., "Medium Slow", "Fast", "Slow")
- `growth_rate_identifier` (e.g., "medium-slow", "fast", "slow")
- `formula` (Text - mathematical formula for exp calculation)

## Egg Groups

### **Breeding compatibility groups**

- `egg_group_id` (Primary Key)
- `egg_group_name` (e.g., "Monster", "Water 1", "Fairy")
- `egg_group_identifier` (e.g., "monster", "water1", "fairy")

## Natures

### **Stat-modifying natures**

- `nature_id` (Primary Key)
- `nature_name` (e.g., "Hardy", "Adamant", "Modest")
- `nature_identifier` (e.g., "hardy", "adamant", "modest")
- `increased_stat` (Enum: "attack", "defense", "special_attack", "special_defense", "speed", null)
- `decreased_stat` (Enum: "attack", "defense", "special_attack", "special_defense", "speed", null)
- `hates_flavor` (String - for Poffin/Pokeblock mechanics)
- `likes_flavor` (String)

## Items

### **All items in the games**

- `item_id` (Primary Key)
- `item_name` (e.g., "Potion", "Ultra Ball", "Leftovers")
- `item_identifier` (e.g., "potion", "ultra-ball", "leftovers")
- `category_id` (Foreign Key → item_categories)
- `cost` (Integer - buy price, null if can't buy)
- `fling_power` (Integer - for Fling move)
- `generation_introduced` (Integer)

## Item Categories

### **Item classification**

- `item_category_id` (Primary Key)
- `category_name` (e.g., "Medicine", "Pokeballs", "Battle Items")
- `category_identifier` (e.g., "medicine", "pokeballs", "battle-items")
