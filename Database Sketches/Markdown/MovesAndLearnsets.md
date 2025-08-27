# Pokemon Database Schema - Moves & Learnsets

## Moves

### **All Pokemon moves**

- `move_id` (Primary Key)
- `move_name` (e.g., "Tackle", "Flamethrower", "Earthquake")
- `move_identifier` (e.g., "tackle", "flamethrower", "earthquake")
- `generation_introduced` (Integer)
- `type_id` (Foreign Key → types)
- `move_damage_class_id` (Foreign Key → move_damage_classes)
- `move_effect_id` (Foreign Key → move_effects)
- `move_effect_chance` (Integer, nullable - percentage chance for secondary effect)
- `contest_type_id` (Foreign Key → contest_types, nullable)
- `contest_effect_id` (Foreign Key → contest_effects, nullable)
- `super_contest_effect_id` (Foreign Key → super_contest_effects, nullable)

## Move Game Data

### **Game-specific move statistics**

- `move_id` (Foreign Key → moves)
- `version_group_id` (Foreign Key → version_groups)
- `power` (Integer, nullable)
- `pp` (Integer - Power Points)
- `accuracy` (Integer, nullable - percentage)
- `priority` (Integer - move priority)
- `target_id` (Foreign Key → move_targets)
- `move_effect_id` (Foreign Key → move_effects)
- `move_effect_chance` (Integer, nullable)

## Move Damage Classes

### **Physical/Special/Status classification**

- `move_damage_class_id` (Primary Key)
- `class_name` (e.g., "Physical", "Special", "Status")
- `class_identifier` (e.g., "physical", "special", "status")

## Move Effects

### **What moves actually do**

- `move_effect_id` (Primary Key)
- `short_effect` (Text - brief description)
- `effect` (Text - detailed mechanical description)

## Move Targets

### **What the move can target**

- `move_target_id` (Primary Key)
- `target_name` (e.g., "One opponent", "All opponents", "User")
- `target_identifier` (e.g., "selected-pokemon", "all-opponents", "user")

## Move Learn Methods

### **How Pokemon learn moves**

- `move_learn_method_id` (Primary Key)
- `method_name` (e.g., "Level up", "TM", "Egg", "Tutor")
- `method_identifier` (e.g., "level-up", "machine", "egg", "tutor")
- `version_group_id` (Foreign Key → version_groups)

## Pokemon Moves

### **Which Pokemon can learn which moves**

- `pokemon_id` (Foreign Key → pokemon)
- `form_id` (Foreign Key → pokemon_forms, nullable)
- `version_group_id` (Foreign Key → version_groups)
- `move_id` (Foreign Key → moves)
- `move_learn_method_id` (Foreign Key → move_learn_methods)
- `level` (Integer, nullable - level learned if level-up)
- `order` (Integer, nullable - for sorting)

## Machines

### **TMs, HMs, TRs**

- `machine_id` (Primary Key)
- `machine_number` (Integer)
- `version_group_id` (Foreign Key → version_groups)
- `item_id` (Foreign Key → items)
- `move_id` (Foreign Key → moves)
- `machine_type` (Enum: "tm", "hm", "tr")

## Move Names

### **Localized move names**

- `move_id` (Foreign Key → moves)
- `language_id` (Foreign Key → languages)
- `name` (String - move name in that language)

## Move Flavor Text

### **Move descriptions in games**

- `move_id` (Foreign Key → moves)
- `version_group_id` (Foreign Key → version_groups)
- `language_id` (Foreign Key → languages)
- `flavor_text` (Text)

## Contest Data (Optional)

### **For Pokemon Contests (Ruby/Sapphire era)**

### Contest Types

- `contest_type_id` (Primary Key)
- `type_name` (e.g., "Cool", "Beauty", "Cute")
- `type_identifier` (e.g., "cool", "beauty", "cute")

### Contest Effects

- `contest_effect_id` (Primary Key)
- `appeal` (Integer)
- `jam` (Integer)
- `flavor_text` (Text)

### Super Contest Effects

- `super_contest_effect_id` (Primary Key)
- `appeal` (Integer)
- `flavor_text` (Text)

## Languages

### **For localization support**

- `language_id` (Primary Key)
- `language_name` (e.g., "English", "Japanese", "French")
- `language_identifier` (e.g., "en", "ja", "fr")
- `iso639` (String - 2-letter language code)
- `iso3166` (String - 2-letter country code)
- `order` (Integer - for UI sorting)
