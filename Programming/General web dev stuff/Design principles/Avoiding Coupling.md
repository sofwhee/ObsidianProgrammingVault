**Coupling:** When one module has to "know" about another module.
## Why?

- Reusable
- Testable
- In highly scalable and maintainable JavaScript applications, any module can be easily swapped out at any time for a different module.
- Avoids single points of failure (app continues even if unable to give delivery time)

## Patterns to Reduce Coupling
(often a variation of so-called Observer Pattern)

### Flight Control Tower (Pub/Sub + Mediator)

Airplanes only communicate with the tower.
Airplanes do not "know" about each other without tower info.

