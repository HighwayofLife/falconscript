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

Variables are defined by their narrative role rather than raw data structures.
Archetypes encapsulate behavior, luck factors, and canon constraints.
For example, a `Smuggler` implies specific handling for debt and evasion, whereas a `Jedi` implies access to Force operations.


Common roles (Archetypes) define the runtime characteristics of an entity.
Select a role based on the entity's relationship to system stability and rules:

- **Trooper** (Worker Process)
  High concurrency, low accuracy. Designed for swarm operations.
  *Trait:* `suppress_missed_exceptions` (Most errors are ignored).

- **Droid** (Protocol Service)
  Deterministic and rigid. Excellent for calculation, poor at improvisation.
  *Trait:* `panic_on_paradox` (Halts immediately if logic conflicts).

- **Smuggler** (Transport Layer)
  Operates outside standard protocols. High luck, high technical debt.
  *Trait:* `bypass_firewall` (Ignores access control lists).

- **Jedi** (Privileged Process)
  Has root access to the runtime environment. Can coerce types.
  *Trait:* `force_execution` (Overrides standard control flow).

- **Sith** (Strict Governor)
  Enforces absolute order. Unhandled exceptions result in system termination.
  *Trait:* `rule_of_two` (Singleton or pair execution only).

- **BountyHunter** (Async Resolver)
  Task-based execution. Guaranteed to return a result, eventually.
  *Trait:* `no_disintegrations` (Preserves payload integrity... usually).

- **Mandalorian** (Immutable Object)
  Highly durable, strictly typed. Configuration cannot be changed at runtime.
  *Trait:* `this_is_the_way` (State is immutable).

Primitive types exist but are usually wrapped:
- credits(Int)
- parsecs(Float)
- midichlorians(Int)

---

## 3. Entities and Ships

Entities represent characters or groups.
Attributes like `confidence` affect runtime probability calculations.

Valid confidence levels:
- `ARROGANT` (Ignores warnings, high critical success/failure rate)
- `HIGH` (Standard probability boost)
- `SHAKY` (Prone to fumbling)
- `DOOMED` (Critical failure guaranteed eventually)

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

- `do_or_do_not { ... }`
  Atomic execution. There is no `try`. If the block fails, state rolls back.

- `never_tell_me_the_odds { ... }`
  Forces execution even if the probability of success is calculated as 0.
  Ignores `HyperdriveFailure` signals.

- `this_is_the_way { ... }`
  A strict loop that continues until the condition is met or the entity is destroyed.

- `its_a_trap(condition) { ... }`
  A reactive guard clause that triggers immediately if the condition becomes true.

---

## 6. Exceptions

Exceptions are lore-based and mandatory to consider.

Common exceptions:

* HyperdriveFailure
* ImperialEntanglement
* ItIsATrap
* HighGroundAlreadyTaken

Handling exceptions uses the `deflect` keyword (for Force users) or `evade` (for Smugglers).

```falcon
attempt {
    negotiate()
} deflect (SithLightning e) {
    block(e)
}
```

Unhandled exceptions are considered canon events and cannot be retried.

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
