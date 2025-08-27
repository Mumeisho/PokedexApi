# Pokemon Database Schema - Locations & Encounters

## Regions

### **Game regions (Kanto, Johto, etc.)**

- `region_id` (Primary Key)
- `region_name` (e.g., "Kanto", "Johto", "Hoenn")
- `region_identifier` (e.g., "kanto", "johto", "hoenn")
- `generation_introduced` (Integer)

## Locations

### **Specific areas within regions**

- `location_id` (Primary Key)
- `location_name` (e.g., "Route 1", "Viridian Forest", "Mt. Silver")
- `location_identifier` (e.g., "route-1", "viridian-forest", "mt-silver")
- `region_id` (Foreign Key → regions)

## Location Areas

### **Sub-areas within locations (grass, cave, water, etc.)**

- `location_area_id` (Primary Key)
- `location_id` (Foreign Key → locations)
- `area_name` (e.g., "Grass", "Cave", "Surfing", "Fishing")
- `area_identifier` (e.g., "grass", "cave", "surfing", "fishing")

## Encounter Methods

### **How Pokemon are encountered**

- `encounter_method_id` (Primary Key)
- `method_name` (e.g., "Walking", "Surfing", "Fishing", "Gift")
- `method_identifier` (e.g., "walk", "surf", "old-rod", "gift")
- `order` (Integer - for UI sorting)

## Encounters

### **Specific Pokemon encounters in games**

- `encounter_id` (Primary Key)
- `pokemon_id` (Foreign Key → pokemon)
- `form_id` (Foreign Key → pokemon_forms)
- `version_group_id` (Foreign Key → version_groups)
- `location_area_id` (Foreign Key → location_areas)
- `encounter_method_id` (Foreign Key → encounter_methods)
- `min_level` (Integer)
- `max_level` (Integer)
- `chance` (Integer - encounter rate percentage)
- `condition_values` (JSON - special conditions like time of day, weather)

## Pokedex Entries

### **Flavor text for each Pokemon**

- `pokemon_id` (Foreign Key → pokemon)
- `form_id` (Foreign Key → pokemon_forms, nullable)
- `version_group_id` (Foreign Key → version_groups)
- `pokedex_number` (Integer - regional dex number)
- `entry_text` (Text - the flavor text)

## Regional Pokedexes

### **Different regional Pokedex listings**

- `pokedex_id` (Primary Key)
- `pokedex_name` (e.g., "National", "Kanto", "Johto", "Galar")
- `pokedex_identifier` (e.g., "national", "kanto", "johto", "galar")
- `region_id` (Foreign Key → regions, nullable)
- `version_group_id` (Foreign Key → version_groups)
- `is_main_series` (Boolean)

## Pokedex Numbers

### **Pokemon numbering in each regional dex**

- `pokemon_id` (Foreign Key → pokemon)
- `pokedex_id` (Foreign Key → regional_pokedexes)
- `pokedex_number` (Integer - number in that specific dex)

## Evolution Chains

### **Evolution family groupings**

- `evolution_chain_id` (Primary Key)
- `baby_trigger_item_id` (Foreign Key → items, nullable)

## Evolution Conditions

### **How Pokemon evolve**

- `evolution_id` (Primary Key)
- `evolved_pokemon_id` (Foreign Key → pokemon)
- `evolution_trigger_id` (Foreign Key → evolution_triggers)
- `trigger_item_id` (Foreign Key → items, nullable)
- `minimum_level` (Integer, nullable)
- `gender_id` (Integer, nullable - 1=female, 2=male)
- `location_id` (Foreign Key → locations, nullable)
- `held_item_id` (Foreign Key → items, nullable)
- `time_of_day` (Enum: "day", "night", nullable)
- `known_move_id` (Foreign Key → moves, nullable)
- `known_move_type_id` (Foreign Key → types, nullable)
- `minimum_happiness` (Integer, nullable)
- `minimum_beauty` (Integer, nullable)
- `minimum_affection` (Integer, nullable)
- `relative_physical_stats` (Integer, nullable - for Hitmon evolutions)
- `party_pokemon_id` (Foreign Key → pokemon, nullable)
- `trade_pokemon_id` (Foreign Key → pokemon, nullable)
- `needs_overworld_rain` (Boolean)
- `turn_upside_down` (Boolean - for Inkay)

## Evolution Triggers

### **Types of evolution triggers**

- `evolution_trigger_id` (Primary Key)
- `trigger_name` (e.g., "Level up", "Trade", "Use item")
- `trigger_identifier` (e.g., "level-up", "trade", "use-item")
