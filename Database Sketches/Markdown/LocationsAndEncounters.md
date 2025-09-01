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
- `chance` (Integer - encounter rate percentage)
- `encounter_conditions_id` (unique)

## Encounter Condition Values

### **Spesific conditions to encounter a pokemon**

- `encounter_condition_value_id`(Primary Key)
- `value_name`(e.g. "Night", "Day", "Raining")
- `value_identifier` (e.g. "night". "day". "raining")

## Encounter Conditions

- `encounter_conditions_id` (Foreign Key → encounter -> encounter_conditions_id)
- `encounter_condition_value_id` (Foreign Key → encounter_condition_value)

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
