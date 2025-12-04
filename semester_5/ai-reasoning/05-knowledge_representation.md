# Knowledge Representation

## Table of Contents

1. [Introduction](#introduction)
2. [Propositional Logic](#propositional-logic)
3. [First-Order Logic](#first-order-logic)
4. [Semantic Networks](#semantic-networks)
5. [Frames](#frames)
6. [Production Rules](#production-rules)
7. [Ontologies](#ontologies)
8. [Description Logics](#description-logics)
9. [Reasoning Methods](#reasoning-methods)
10. [Knowledge Graphs](#knowledge-graphs)

---

## Introduction

**Knowledge Representation (KR)** is the field of AI concerned with representing information about the world in a form that a computer system can utilize to solve complex tasks.

### Goals of Knowledge Representation

1. **Expressiveness**: Ability to represent complex knowledge
2. **Efficiency**: Fast inference and reasoning
3. **Modularity**: Easy to update and maintain
4. **Understandability**: Human-readable when possible

### Types of Knowledge

- **Declarative**: Facts about the world ("Paris is the capital of France")
- **Procedural**: How to do things (algorithms, rules)
- **Meta-knowledge**: Knowledge about knowledge
- **Heuristic**: Rules of thumb, best practices
- **Structural**: Relationships between concepts

---

## Propositional Logic

### Syntax

**Atomic propositions**: Variables that can be true or false (P, Q, R)

**Logical connectives**:
- **Negation**: ¬P (NOT P)
- **Conjunction**: P ∧ Q (P AND Q)
- **Disjunction**: P ∨ Q (P OR Q)
- **Implication**: P → Q (IF P THEN Q)
- **Biconditional**: P ↔ Q (P IF AND ONLY IF Q)

### Semantics

**Truth tables** define the meaning of connectives:

| P | Q | ¬P | P ∧ Q | P ∨ Q | P → Q | P ↔ Q |
|---|---|-------|-------|-------|-------|-------|
| T | T | F | T | T | T | T |
| T | F | F | F | T | F | F |
| F | T | T | F | T | T | F |
| F | F | T | F | F | T | T |

### Inference Rules

**Modus Ponens**:
```
P → Q
P
-------
∴ Q
```

**Modus Tollens**:
```
P → Q
¬Q
-------
∴ ¬P
```

**Resolution**:
```
P ∨ Q
¬P ∨ R
-----------
∴ Q ∨ R
```

### Limitations

- Cannot express relationships between objects
- Cannot quantify over objects
- Limited expressiveness for real-world knowledge

---

## First-Order Logic

### Components

**Constants**: Specific objects (john, paris, 5)

**Variables**: Placeholders (x, y, z)

**Predicates**: Relations or properties
- Unary: Person(x) - "x is a person"
- Binary: Parent(x, y) - "x is parent of y"
- n-ary: Between(x, y, z) - "x is between y and z"

**Functions**: Map objects to objects
- father(x) - "the father of x"
- age(x) - "the age of x"

**Quantifiers**:
- **Universal**: ∀x P(x) - "for all x, P(x) is true"
- **Existential**: ∃x P(x) - "there exists an x such that P(x) is true"

### Example Sentences

1. "All humans are mortal":
   ```
   ∀x (Human(x) → Mortal(x))
   ```

2. "Socrates is human":
   ```
   Human(socrates)
   ```

3. "Every person has a mother":
   ```
   ∀x (Person(x) → ∃y (Mother(y, x)))
   ```

4. "John loves everyone who loves Mary":
   ```
   ∀x (Loves(x, mary) → Loves(john, x))
   ```

### Inference in FOL

**Universal Instantiation**:
```
∀x P(x)
---------
P(c)  [for any constant c]
```

**Existential Instantiation**:
```
∃x P(x)
---------
P(c)  [for some new constant c]
```

**Unification**: Finding substitutions that make different expressions identical

**Resolution Theorem Proving**: Convert to CNF and apply resolution

---

## Semantic Networks

**Semantic networks** represent knowledge as a directed graph with:
- **Nodes**: Concepts, objects, events
- **Edges**: Relationships between nodes

### Common Relationships

- **IS-A**: Taxonomic hierarchy (Bird IS-A Animal)
- **HAS-A**: Part-whole (Car HAS-A Engine)
- **INSTANCE-OF**: Object-class (Tweety INSTANCE-OF Bird)
- **PROPERTY**: Attributes (Bird PROPERTY CanFly)

### Example

```
Animal
  |
  IS-A
  |
Bird ----HAS-A----> Wings
  |                    |
  |                PROPERTY
  |                    |
INSTANCE-OF        CanFly
  |
Tweety
```

### Advantages

- Intuitive visual representation
- Easy to navigate and extend
- Supports inheritance

### Limitations

- Ambiguous semantics
- Difficult to represent complex relations
- No standard inference mechanism

---

## Frames

**Frames** are data structures representing stereotypical situations or objects.

### Structure

```
Frame: Car
  IS-A: Vehicle
  HAS-A: 
    - Engine (required)
    - Wheels (default: 4)
    - Color (default: unknown)
  ACTIONS:
    - Drive
    - Park
  CONSTRAINTS:
    - NumberOfWheels >= 3
```

### Components

- **Frame name**: Identifier
- **Slots**: Attributes or properties
- **Fillers**: Values for slots
- **Facets**: Additional information about slots
  - Default values
  - Constraints
  - Procedural attachments (demons)

### Inheritance

Frames can inherit slots from parent frames:

```
Frame: Vehicle
  HAS-A: Engine
  CAN: Move

Frame: Car
  IS-A: Vehicle
  HAS-A: Wheels (default: 4)
  
Frame: MyCar
  INSTANCE-OF: Car
  Color: Blue
  Wheels: 4 (inherited default)
  Engine: (inherited from Vehicle)
```

---

## Production Rules

**Production rules** represent knowledge as condition-action pairs:

```
IF <condition> THEN <action>
```

### Examples

1. **Medical diagnosis**:
   ```
   IF patient has fever AND patient has cough
   THEN patient may have flu
   ```

2. **Expert system**:
   ```
   IF temperature > 100°C AND pressure > 5 bar
   THEN reduce temperature AND alert operator
   ```

### Forward Chaining

**Data-driven reasoning**:
1. Start with known facts
2. Apply rules whose conditions are satisfied
3. Add conclusions to knowledge base
4. Repeat until goal reached or no rules apply

### Backward Chaining

**Goal-driven reasoning**:
1. Start with goal to prove
2. Find rules that conclude the goal
3. Try to prove the conditions of those rules
4. Recursively work backward

### Conflict Resolution

When multiple rules can fire:
- **Specificity**: More specific rules first
- **Recency**: Recently added facts first
- **Priority**: Explicitly assigned priorities

---

## Ontologies

**Ontology**: Formal specification of a shared conceptualization.

### Components

1. **Classes**: Categories of things
2. **Instances**: Specific examples
3. **Attributes**: Properties
4. **Relations**: Connections between classes
5. **Axioms**: Rules and constraints

### Web Ontology Language (OWL)

**OWL** is a standard for representing ontologies on the web.

**Example**:
```xml
<owl:Class rdf:ID="Person">
  <rdfs:subClassOf rdf:resource="#Animal"/>
</owl:Class>

<owl:Class rdf:ID="Student">
  <rdfs:subClassOf rdf:resource="#Person"/>
</owl:Class>

<owl:ObjectProperty rdf:ID="hasAdvisor">
  <rdfs:domain rdf:resource="#Student"/>
  <rdfs:range rdf:resource="#Professor"/>
</owl:ObjectProperty>
```

### Applications

- **Semantic Web**: Interoperability between systems
- **Information retrieval**: Enhanced search
- **Data integration**: Merging heterogeneous data sources
- **Natural language processing**: Understanding text

---

## Description Logics

**Description Logics (DL)** are a family of formal knowledge representation languages.

### Basic Constructors

- **Concept names**: Person, Animal
- **Role names**: hasChild, likes
- **Individuals**: john, mary

**Constructors**:
- **Intersection**: C ⊓ D (C AND D)
- **Union**: C ⊔ D (C OR D)
- **Negation**: ¬C (NOT C)
- **Exists restriction**: ∃R.C (has some R-relation to C)
- **Value restriction**: ∀R.C (all R-relations to C)

### Example Definitions

1. **Mother**: Woman who has a child
   ```
   Mother ≡ Woman ⊓ ∃hasChild.Person
   ```

2. **Parent**: Person with at least one child
   ```
   Parent ≡ Person ⊓ ∃hasChild.Person
   ```

3. **Grandparent**: Person whose child is a parent
   ```
   Grandparent ≡ Person ⊓ ∃hasChild.Parent
   ```

### Reasoning Tasks

- **Subsumption**: Is concept A more general than B?
- **Classification**: Organize concepts into hierarchy
- **Instantiation**: Does individual belong to concept?
- **Consistency**: Is knowledge base contradictory?

---

## Reasoning Methods

### Deductive Reasoning

**From general to specific**:
```
All humans are mortal (general)
Socrates is human
Therefore, Socrates is mortal (specific)
```

### Inductive Reasoning

**From specific to general**:
```
Swan 1 is white
Swan 2 is white
Swan 3 is white
Therefore, all swans are white (generalization)
```

**Note**: Conclusions are probable, not certain.

### Abductive Reasoning

**Inference to best explanation**:
```
The grass is wet
If it rained, the grass would be wet
Therefore, it probably rained
```

### Default Reasoning

**Reasoning with typical cases**:
```
Birds typically fly
Tweety is a bird
Therefore, Tweety flies (unless told otherwise)
```

**Non-monotonic**: Conclusions can be retracted with new information.

### Analogical Reasoning

**Reasoning by similarity**:
```
Atoms are like solar systems
Electrons orbit nucleus like planets orbit sun
Therefore, atomic structure might follow similar laws
```

---

## Knowledge Graphs

**Knowledge graphs** represent entities and their relationships as a graph.

### Structure

- **Nodes**: Entities (people, places, concepts)
- **Edges**: Relationships (directed, labeled)
- **Attributes**: Properties of entities

### Triple Representation

Knowledge expressed as subject-predicate-object triples:

```
(Barack Obama, born in, Hawaii)
(Barack Obama, was, President)
(Barack Obama, spouse, Michelle Obama)
```

### Popular Knowledge Graphs

- **Google Knowledge Graph**: Powers search results
- **DBpedia**: Structured Wikipedia data
- **Wikidata**: Collaborative knowledge base
- **YAGO**: Semantic knowledge base
- **ConceptNet**: Common sense knowledge

### Applications

- **Search engines**: Enhanced results with entity information
- **Question answering**: Direct answers from structured data
- **Recommendation systems**: Content and product suggestions
- **Data integration**: Linking disparate data sources
- **Conversational AI**: Context-aware dialogue systems

### Graph Queries

**SPARQL** is the standard query language:

```sparql
SELECT ?person ?birthPlace
WHERE {
  ?person rdf:type :Person .
  ?person :bornIn ?birthPlace .
  ?birthPlace :locatedIn :USA .
}
```

---

## Practical Considerations

### Choosing a Representation

**Factors to consider**:
1. **Domain complexity**: Simple vs. complex relationships
2. **Reasoning requirements**: What inferences are needed?
3. **Computational efficiency**: Speed vs. expressiveness trade-off
4. **Maintenance**: Ease of updating knowledge
5. **Integration**: Compatibility with other systems

### Comparison Table

| Representation | Expressiveness | Inference Speed | Human Readability | Use Cases |
|----------------|----------------|-----------------|-------------------|-----------|
| Propositional Logic | Low | Fast | Medium | Simple Boolean reasoning |
| First-Order Logic | High | Slow | Low | Complex logical reasoning |
| Semantic Networks | Medium | Medium | High | Taxonomies, inheritance |
| Frames | Medium | Fast | High | Object-oriented domains |
| Production Rules | Medium | Fast | High | Expert systems, control |
| Ontologies | High | Medium | Medium | Semantic web, integration |
| Description Logics | High | Medium | Low | Formal reasoning |
| Knowledge Graphs | High | Fast | High | Large-scale data, search |

---

## Common Challenges

### Knowledge Acquisition Bottleneck

- Difficulty extracting knowledge from experts
- Time-consuming manual encoding
- **Solutions**: Machine learning, crowdsourcing, automated extraction

### Uncertainty and Incompleteness

- Real-world knowledge is often uncertain
- Information may be missing or contradictory
- **Solutions**: Probabilistic reasoning, fuzzy logic, Bayesian networks

### Scalability

- Large knowledge bases can be difficult to manage
- Inference can become computationally expensive
- **Solutions**: Indexing, caching, approximate reasoning

### Maintenance and Evolution

- Knowledge changes over time
- Keeping KB consistent and up-to-date
- **Solutions**: Version control, automated validation, incremental updates

---

## Summary

- **Knowledge representation** is fundamental to AI systems
- **Multiple formalisms** exist, each with trade-offs
- **Propositional and first-order logic** provide formal foundations
- **Semantic networks and frames** offer intuitive structures
- **Production rules** enable practical expert systems
- **Ontologies** facilitate knowledge sharing and interoperability
- **Description logics** balance expressiveness and decidability
- **Knowledge graphs** power modern search and AI applications
- **Choice of representation** depends on domain, requirements, and constraints
- **Reasoning methods** vary from deductive to probabilistic
- **Practical challenges** include acquisition, uncertainty, and scalability