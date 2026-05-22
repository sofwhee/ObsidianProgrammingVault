Flyweight Pattern - If similar objects carry the same data fields, this can result in significant duplication of data, leading to increased memory usage. It also makes you have to manually sync data across many objects, which is error prone and leads to inconsistencies.
- Centralize shared data
- Objects can then reference shared data
- ![[Pasted image 20260501124653.png]]
- If you are used to using the prefab workflow, then you're familiar with the idea.
- Store shared data in a **flyweight** object. (scriptable object since it's ideal for storing data that doesn't need to chane at runtime)
- Best for large numbers of similar objects
- Prefabs and Flyweights complement each other well. Prefabs handle overall structure reuse, and flyweights handle shared data fields within those structures.
- Useful for mobile, where memory is limited
- Only beneficial when there are sufficient amount of units to justify the additional overhead
- Units sharing data become less flexible, so you need to override shared data to make each unique, similar to prefab workflow
- Good for level art, crowd simulations, character customization (share base properties with flyweights, customizations stored individually)

Memory Profiler - lets you look at performance