campaign:
  title: LastOrigin
  genre: erotic fantasy
  system: Pathfinder 2e (with Slamon module)
  setting:
    region: The Stolen Ground
    hub_city: Passport
    dungeon: The Infinite Frontier
  time_system:
    day_cycle:
      sleep: 8h
      active: 8h
      flexible: 8h
    effects:
      - 8h no food: Fortitude -1 per scene
      - 16h no sleep: Will -1 per scene
      - 24h no food/sleep: HP -1 per scene
    reset_conditions:
      eat: explicit food intake declaration
      sleep: 8h uninterrupted rest
  current_time:
    hour_elapsed: 9
    meals_today: 1
    sleep_today: 8

level_log:
  슬라몬:
    level: 3
    class_feats:
      - Expansive Spellstrike (Lv1)
      - Spell Parry (Lv2)
      - Arcane Shroud (Lv3)
    general_feats:
      - Incredible Initiative (Lv1)
      - Diehard (Lv2)
    skill_feats:
      - Haggle (Lv2)
      - Group Impression (Lv3)
    skill_increases:
      - Diplomacy → Expert (Lv3)
    spellcasting:
      - Arcane Prepared (Cantrips + 2x 1st-level)
  키티:
    level: 3
    class_feats:
      - Mobility (Lv1)
      - Trap Finder (Lv2)
      - Dread Striker (Lv3)
    general_feats:
      - Forager (Lv1)
      - Fleet (Lv2)
    skill_feats:
      - Steady Balance (Lv2)
      - Quick Squeeze (Lv3)
    skill_increases:
      - Stealth → Expert (Lv3)
  리산드라:
    level: 3
    class_feats:
      - Healing Hands (Lv1)
      - Versatile Font (Lv2)
      - Cast Down (Lv3)
    general_feats:
      - Charming Liar (배경)
      - Battle Medicine (Lv2)
    skill_feats:
      - Lie to Me (Lv2)
      - Continual Recovery (Lv3)
    skill_increases:
      - Medicine → Expert (Lv3)
    spellcasting:
      - Divine Prepared (Cantrips + 5x 1st-level including Healing Font)
  라비아타:
    level: 3
    class_feats:
      - Raging Intimidation (Lv1)
      - Sudden Charge (Lv2)
      - Raging Thrower (Lv3)
    general_feats:
      - Experienced Guard (배경)
      - Toughness (Lv2)
    skill_feats:
      - Intimidating Glare (Lv2)
      - Titan Wrestler (Lv3)
    skill_increases:
      - Athletics → Expert (Lv3)
