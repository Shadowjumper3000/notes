I. Introduction and Commitment
First-Order Logic (FOL) represents a refinement over procedural programming and propositional logic
.
A. Advantages of Declarative Programming/Logic
Declarative programming and propositional logic offer three key benefits
:
1. Inference independent of domain: New facts can be derived from existing facts
.
2. Expressiveness for partial information: The system can state that one thing or another is true
.
3. Compositionality: The meaning of a sentence is determined by the meaning of its component parts
.
B. The Role of FOL
FOL attempts to approximate natural language and offers more succinct representations compared to propositional logic
. It is fundamentally built around objects and relationships. Properties of an object are treated as unitary relations
.
C. Commitments
Logic systems make commitments regarding the nature of reality and the states of knowledge allowed
:
Commitment Type
	
Propositional Logic
	
First-Order Logic
	
Probability Theory
Ontological (What exists)
	
Facts
	
Facts, objects, relations
	
N/A
Epistemological (States of knowledge)
	
True, False, Unknown
	
True, False, Unknown
	
Degree of belief/subjective likelihood
II. First-Order Logic: Representation
A. Models and Domain
FOL representations rely on Models, which contain objects
.
• The Domain is the set of objects or domain elements within the model
.
• The Domain cannot be empty
.
• Objects can be related in various ways
. Examples of domain elements include Richard the Lionheart, King John, a crown, and the left legs of Richard and John
.
B. Relationships
Relationships can be expressed as
:
• A tuple (an ordered set of objects that are related), e.g., Brothers: {<Richard, John>, <John, Richard>}
.
• A function, which should ideally be total (have a value for every input), e.g., Left leg: <Richard> → Richard's left leg
.
C. Symbols and Interpretation
Symbols are used to represent elements of the domain and relationships
:
• Constant symbols stand for objects (e.g., Richard, John)
.
• Predicate symbols stand for relations and have arity (e.g., Brother, OnHead)
.
• Function symbols stand for functions and have arity (e.g., LeftLeg)
.
A model uses an interpretation to specify which objects, relations, and functions are referenced by these symbols (the intended interpretation)
.
D. Sentence Structure
1. Terms: A logical expression that refers to a specific object (e.g., LeftLeg(John))
.
2. Atomic sentences (atom): A predicate symbol combined with optional terms (e.g., Brother(Richard, John))
. An atomic sentence is true in a model if the specified relationship holds true among the objects referred to by the arguments
.
3. Complex sentences: Sentences combined using logical connectives (e.g., King(Richard)∨King(John))
.
E. Quantification
FOL uses quantifiers to express properties over collections of objects
:
• Universal Quantification (∀, "for all"): ∀xP is true if the proposition P is true across all possible extended interpretations of the variable x
.
    ◦ Example: ∀xKing(x)⇒Person(x) is true if, for every domain element, if that element is a king, it is also a person
.
• Existential Quantification (∃, "for some"): ∃xP is true if P is true in at least one extended interpretation where x is assigned to a domain element
.
    ◦ Example: ∃xCrown(x)∧OnHead(x,John) is true if there is at least one object that is a crown and is on John's head
.
• Nested Quantification: Quantifiers can appear consecutively (∀x,yBrother(x,y)⇒Sibling(x,y)) or mixed, requiring parentheses for clarity (∀x(∃yLoves(x,y)))
.
• Equality: The equality sign signifies that two terms refer to the same object
.
F. Quantifier Relationship and De Morgan Rules
Universal and existential quantifiers are connected via negation
. De Morgan rules relate these concepts
:
Quantifier Relationship
	
Propositional Equivalent
∀x¬P≡¬∃xP
	
¬(P∨Q)≡¬P∧¬Q
¬∀xP≡∃x¬P
	
¬(P∧Q)≡¬P∨¬Q
∀xP≡¬∃x¬P
	
P∧Q≡¬(¬P∨¬Q)
∃xP≡¬∀x¬P
	
P∨Q≡¬(¬P∧¬Q)
III. First-Order Logic: Usage
A. Database Semantics
When used as a database, FOL often employs specific semantic assumptions
:
• Unique-names assumption: Every constant symbol refers to a distinct object
.
• Closed-world assumption: Atomic sentences that are not known to be true are assumed false
.
• Domain closure: Each model contains no more domain elements than those specifically named by the constant symbols
.
B. Knowledge Base Interaction
• Assertions: Sentences are added to the Knowledge Base (KB) using the TELL command (e.g., TELL(KB,King(John)))
.
• Queries: Questions are asked using ASK (e.g., ASK(KB,King(John)))
.
• Quantified Queries: Queries can contain quantifiers. The command ASKVARS can return substitution or binding lists (e.g., ASKVARS(KB,Person(x)) returns {x/John} and {x/Richard})
.
C. Axioms and Representation
• Axioms form the basis of factual information
. They can function as definitions (∀x,yP(x,y)⇔…), partial specifications (∀xP(x)⇒…), or simply descriptions of specific instances/facts
.
• Theorems are facts entailed by the axioms; while not mandatory in the KB, they can help reduce computational cost
.
• FOL can be used to represent complex structures like numbers, sets, and lists
. The sources provide example axioms for natural numbers using the successor function, S(n)
.
• For complex scenarios like the Wumpus world, FOL provides a more succinct description by quantifying over time and using coordinates
.
IV. First-Order Logic: Inference
A. Instantiation Methods
Inference often requires removing universal or existential quantifiers through instantiation
:
1. Universal Instantiation (UI): Allows inferring any sentence by substituting a ground term (a term without variables) for a universally quantified variable (∀vα→SUBST({v/g},α))
.
2. Existential Instantiation (EI): Replaces an existentially quantified variable with a single new constant symbol (∃vα→SUBST({v/k},α))
.
B. Propositionalization
This method applies UI and EI and then replaces atomic symbols (e.g., King(John)) with proposition symbols (e.g., JohnIsKing)
. This approach is complete but only semidecidable; it is impossible to know if a lack of entailment is due to requiring deeper search or true impossibility. Function symbols can create a challenge due to the potential for infinite substitutions (e.g., Father(Father(John))), often requiring iterative deepening
.
C. Generalized Modus Ponens (GMP)
GMP lifts the concept of Modus Ponens from propositional logic to FOL
. If p1′​,p2′​,…,pn′​ and the implication (p1​∧p2​∧⋯∧pn​⇒q) are known, and a substitution θ exists such that SUBST(θ,pi′​)=SUBST(θ,pi​) for all i, then the conclusion SUBST(θ,q) can be inferred
.
D. Unification
Unification is the process of finding the substitution θ that makes two logical expressions (p and q) identical: UNIFY(p,q)=θ where SUBST(θ,p)=SUBST(θ,q)
.
• Variables must be standardized apart (given different names) to avoid failure during unification
.
• The goal is to find the Most General Unifier (MGU), which imposes the fewest restrictions on the variables
. A simple quadratic time algorithm exists for this process
.
E. Resolution
Resolution in FOL uses Conjunctive Normal Form (CNF), where sentences are conjunctions of clauses, and each clause is a disjunction of literals, with variables implicitly universally quantified
.
Steps for converting to CNF include
:
1. Eliminating implications (e.g., P⇒Q becomes ¬P∨Q).
2. Moving negation (¬) inwards.
3. Standardizing variables (replacing repeated ones with new ones).
4. Skolemization: Using functions instead of variables during Existential Instantiation
.
5. Dropping universal quantifiers.
6. Distributing ∨ over ∧
.
Resolution Inference Rule: Two clauses, assumed to be standardized apart, can be resolved if they contain complementary literals (one unifies with the negation of the other)
. If UNIFY(li​,¬mj​)=θ, a new resolvent clause is produced by applying the substitution θ to the disjunction of the remaining literals
.

--------------------------------------------------------------------------------
Analogy for FOL: Think of First-Order Logic as a sophisticated building code for knowledge. Propositional Logic is like a list of simple facts about materials ("This wire is hot," "This wall is load-bearing"). FOL allows you to describe relationships between objects and generalize those facts. It’s like saying, "For all steel beams (∀x SteelBeam(x)), the stress resistance is a function of its dimensions (Resistance(x)=f(dimensions))." It provides the rules for defining structure, relationships, and the derived conclusions, enabling complex, realistic models of reality within a formal framework.