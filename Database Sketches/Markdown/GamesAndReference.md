# Pokemon Database Schema - Games & Reference Data

## Games

### **All Pokemon games and versions**

- `game_id` (Primary Key)
- `game_name` (e.g., "Red", "Blue", "Sword", "Violet")
- `game_identifier` (e.g., "red", "blue", "sword", "violet")
- `generation` (Integer - 1-9)
- `version_group_id` (Foreign Key → version_groups)
- `release_date` (Date)
- `platform` (Foreign Key → platforms)
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

## Platforms

### **Nintendo Hardware List**

- `platform_id` (Primary Key)
- `platform_name`(e.g., "Nintendo Switch", "Nintendo WiiU")
- `platform_identifier`(e.g., "nintendo-switch", "nintendo-wii-u)

## Relations

### **Pokemon relation Groups**

- `relation_group_id` (Primary Key)
- `relation_name` (e.g. "Firefly Duo", "Sea Guardians")
- `relation_identifier`(e.g. "firefly_duo", "sea_guardians")
- `relation_description` (Description of this group's relation to eachother. Not evolution related)
