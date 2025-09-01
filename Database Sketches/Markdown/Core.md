# Pokemon Database Schema - Core Tables

## Pokemon (Species Level)

### **Universal information that doesn't change across games/forms**

- `pokemon_id` (Primary Key)
- `national_id` (Unique - National Dex number)
- `species_name` (e.g., "Pikachu", "Charizard")
- `classification` (e.g., "Mouse Pokemon", "Flame Pokemon")
- `gender_ratio` (Float - 0.0 = all male, 1.0 = all female, -1 = genderless)
- `evolution_chain_id` (Foreign Key → evolution_chains)
- `relation_group_id`(Foreign Key → relation_groups, nullable)
- `generation_introduced` (Integer - 1-9)
- `is_legendary` (Boolean)
- `is_mythical` (Boolean)
- `is_baby` (Boolean)
- `capture_rate` (Integer)
- `base_happiness` (Integer)
- `growth_rate_id` (Foreign Key → growth_rates)
- `egg_group_1_id` (Foreign Key → egg_groups)
- `egg_group_2_id` (Foreign Key → egg_groups, nullable)
- `hatch_cycles` (Integer)

## Pokemon Forms

### **Different forms/variants of the same species**

- `form_id` (Primary Key)
- `pokemon_id` (Foreign Key → pokemon)
- `form_name` (e.g., "Base", "Alolan", "Galarian", "Attack Forme")
- `form_identifier` (e.g., "base", "alolan", "galarian", "attack")
- `form_type` (Enum: "base", "regional_variant", "alternate_form", "mega", "gigantamax", "shiny")
- `is_default` (Boolean - true for the base form)
- `is_battle_only` (Boolean - true for Mega evolutions, etc.)
- `sprite_name` (String - for image file naming)

## Pokemon Form Games

### **Game-specific data for each form**

- `pokemon_form_game_id` (Primary Key)
- `pokemon_id` (Foreign Key → pokemon)
- `form_id` (Foreign Key → pokemon_forms)
- `game_id` (Foreign Key → games)
- `is_available` (Boolean)
- `is_shiny_locked` (Boolean)
- `height` (Float - in meters)
- `weight` (Float - in kg)
- `base_experience` (Integer)
- `hp` (Integer)
- `attack` (Integer)
- `defense` (Integer)
- `special_attack` (Integer)
- `special_defense` (Integer)
- `speed` (Integer)

## Pokemon Form Game Types

### **Type assignments for each form/game combination**

- `pokemon_form_game_id` (Foreign Key → pokemon_form_games)
- `type_id` (Foreign Key → types)
- `slot` (Integer - 1 or 2, for primary/secondary type)

## Pokemon Form Game Abilities

### **Ability assignments for each form/game combination**

- `pokemon_form_game_id` (Foreign Key → pokemon_form_games)
- `ability_id` (Foreign Key → abilities)
- `slot` (Integer - 1, 2, or 3 for hidden ability)
- `is_hidden` (Boolean)
