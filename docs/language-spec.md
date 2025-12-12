# FalconScript Language Specification

## 1. Structure

- A source file is an `episode`
- Episodes may be grouped under an `era`
- Execution begins at `scene main()` if present

Valid eras include:
- HIGH_REPUBLIC
- FALL_OF_JEDI
- AGE_OF_EMPIRE
- NEW_REPUBLIC
- FIRST_ORDER

---

## 2. Types

FalconScript favors archetypes over primitives.

Common roles:
- Jedi
- Sith
- Smuggler
- Mandalorian
- Droid
- BountyHunter
- RebelCell

Primitive types exist but are usually wrapped:
- credits(Int)
- parsecs(Float)
- midichlorians(Int)

---

## 3. Entities and Ships

Entities represent characters or groups.

```falcon
entity HanSolo : Smuggler {
    confidence = HIGH
    debt = credits(1000000)
}
````

Ships are special entities with unreliable subsystems.

```falcon
ship MillenniumFalcon {
    hyperdrive = "temperamental"
    condition = "functional-ish"
}
```

---

## 4. Scenes

Scenes are execution units.
State persists across scenes unless retconned.

```falcon
scene board_ship() {
    load_cargo()
}
```

---

## 5. Control Flow

Standard control flow exists but is discouraged.

Preferred constructs:

* `never_tell_me_the_odds()`
* `this_is_the_way()`
* `its_a_trap()`

These alter execution probability and branching behavior.

---

## 6. Exceptions

Exceptions are lore-based and mandatory to consider.

Common exceptions:

* HyperdriveFailure
* ImperialEntanglement
* ItIsATrap
* HighGroundAlreadyTaken

Unhandled exceptions are considered canon events.

---

## 7. Retcons

Reality may be rewritten using explicit annotations.

```falcon
@retcon("Special Edition")
```

Retcons increase narrative instability and should be used sparingly.

---

## 8. Determinism

* Syntax is deterministic
* Parsing is deterministic
* Compilation is strict
* Runtime behavior is influenced by narrative state

This is intentional.

